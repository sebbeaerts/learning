# commandLine #

## From the command line, you can navigate through files and folders on your computer: ##

pwd = "printing working directory"
ls = "list files"
cd ^argument = "change directory"

cd jan/memory/ = goes deeper in the tree.
cd .. = goes up in the tree.

mkdir ^argument = "make directory" 

touch ^argument = Creates a new file inside the working directory. filename as argument.

- pwd: outputs the name of the current working directory.
- ls: lists all files and directories in the working directory.
- cd: switches you into the directory you specify.
- mkdir: creates a new directory in the working directory.
- touch: creates a new file inside the working directory.

## learn how to list files in terminal ##

ls -a 
ls => list files and directories in the working directory 
-a => modifies the behavior of the ls command to also list the files and directories starting with a dot. Files started with a dot are hidden, and don't appear when using ls alone.
   => -a is called an option. Options modify the behavior of commands.

More options for ls command :
- -a list all contents including hidden files and directories
- -l list all contents of a directory in long format
- -t order files and directories by the time they were last modified.

- -alt lists all contents togheter

## learn how to copy files in terminal ##

- cp = copy file
- cp ^sourcefile ^destination directory 
- cp * ^directory = selects all files in the working directory and copies them to the directory.
- cp m*.txt ^directory = selects all files in the working directory starting with m and ending with .txt and copies them to the directory.

## learn how to rename and move files in terminal ##

- mv ^filename ^directory = moves the file in working directory to the directory. first argument is the source file and the destination directory as the second argument.
- mv ^filename ^filename ^directory = To move multiple files into a directory, use mv with a list of source files as the first arguments, and the destination directory as the last argument.
- mv ^filename ^newfilename = rename the file in the newfilename.

## learn how to remove files in terminal ##

- rm ^filename = rm command deletes files and directories. 
- rm -r ^directory = -r is an option that modifies the behavior of the rm command. The -r stands for "recursive," and it's used to delete a directory and all of its child directories.

## summary ##

### Options modify the behavior of commands: ###

- ls -a lists all contents of a directory, including hidden files and directories
- ls -l lists all contents in long format
- ls -t orders files and directories by the time they were last modified
- Multiple options can be used together, like ls -alt

### From the command line, you can also copy, move, and remove files and directories: ###

- cp copies files
- mv moves and renames files
- rm removes files
- rm -r removes directories

### Wildcards are useful for selecting groups of files and directories ###

## Focus on input and output I/O redirection ## 

- stdin = standard input
- stdout = standard output
- stderr = standard error

- > command redirects the standard output to a file
- cat command outputs the contents of a file to the terminal.
- cat file > file = takes the standard output of the command on the left, and redirects it to the file on the right. > overwrites all original content in the right file.
- cat file >> file = takes the standard output of the command on the left and appends(adds) it to the file on the right.
- cat < file = takes the standard input from the file on the right and inputs it into the program on the left.

- | = is a "pipe". The | takes the standard output of the command on the left, and pipes it as standard input to the command on the right. 
- wc = the wc command outputs the number of lines, words an characters in a file. 

- sort ^filename = sort takes the standard input and orders it alphabetically for the standard output.
- cat ^filename | sort > ^otherfilename = the command takes the standard output from cat filename and "pipes" it to sort. The standard output of sort is redirected to the otherfile.

- uniq ^filename = uniq stands for "unique" and filters out adjacent, duplicate lines in a file.
- sort ^filename | uniq = a more effective way to call uniq is to call sort to alphabetize a file, and "pipe" the standard output to uniq. all duplicate lines are alphabetized and filtered out.
- sort ^filename.txt | uniq > ^otherfilename = Here we simply send filtered contents to the otherfilename wich you can view with cat command.

- grep = "global regular expression print"
- grep ^pattern ^filename = it searches files for lines that match a pattern and returns the results. It is also case sensitive.
- grep -i ^pattern ^filename = grep -i => enables the command to be case insensitive. 

- grep -R ^pattern ^pathfile = grep -R => searches all files in a directory and outputs filenames and lines containing matched results. -R stands for "recursive".
- grep -Rl ^pattern ^pathfile = searches all files in a directory and outputs only filenames with matched results. -R stands for "recursive" and l stands for "files with matches".

- sed = stands for "stream editor". It accepts standard inputs and modifies it based on an expression, before displaying it as output data. It is similar to "find and replace".

Let's look at the expression 's/^string/^string2/':
- s: stands for "substitution". it is always used when using sed for substitution.
- string: the search string, the text to find.
- string2: the replacement string, the text to add in place.

=> the command above will only replace the first instance of string on a line.

-sed 's/^string/^string2/g' ^filename = this command uses the g expression, meaning "global". Here sed searches filename for the word "string" and replaces it wit "string2", globally. All instances of "snow" on a line will be turned to "rain".

## Summary ##

### Redirection reroutes standard input, standard output, and standard error.
The common redirection commands are: ###

> redirects standard output of a command to a file, overwriting previous content.
>> redirects standard output of a command to a file, appending new content to old content.
< redirects standard input to a command.
| redirects standard output of a command to another command.
A number of other commands are powerful when combined with redirection commands:

sort: sorts lines of text alphabetically.
uniq: filters duplicate, adjacent lines of text.
grep: searches for a text pattern and outputs it.
sed : searches for a text pattern, modifies it, and outputs it.

## learn how to use the bash profile to configure the environment ##

- nano ^filename = opens a new text file named ^filename in the nano text editor.
- ctrl + O = saving
- enter
- ctrl + X = exit nano text editor.
- ctrl + G = opens a help menu.
- clear = clears the terminal window, moving the command prompt to the top of the screen.

- nano ~/.bash_profile
~ => represents the user's home directory.
. => indicates a hidden file. 
echo "Welcome, Jane Doe" => creates a greeting in the bash profile, which is saved. IT tells the command line to echo the string "Welcome, Jane Doe" when a terminal session begins.
- source ~/.bash_profile = activates the changes in ~/.bash_profile for the current session. Instead of closing the terminal and needing to start a new session, source makes the changes available right away in the session we are in.

- alias pd="pwd" = the alias command allows you to create keyboard shortcuts, or aliases, for commonly used commands.
=> creates the alias pd for the pwd command, which is then saved in the bash profile. Each time you enter pd, the output will be the same as the pwd command.
- source ~/.bach_profile makes the alias pd available in the current session.
=> Each time we open up the terminal, we can use the pd alias.

- export USER="Jane Doe" 
=> The line USER="Jane Doe" sets the environment variable USER to a name "Jane Doe". Usually the USER variable is set to the name of the computer's owner.
=> The line export makes the variable to be available to all child sessions initiated from the session you are in. This is a way to make the variable persist across programs.
- $User
=> At the command line, the command echo $USER returns the value of the variable. Note that $ is always used when returning a variable's value. Here, the command echo $USER returns the name set for the variable.

- export PS1=">> "
=> PS1 is a variable that defines the makeup and style of the command prompt.
=> export PS1=">> " sets the command prompt variable and exports the variable. Here we change the default command prompt from $ to >>.
=> After using the source command, the command line displays the new command prompt.

- $ echo $HOME
=> The HOME variable is an environment variable that displays the path of the home directory. Here by typing echo $HOME, the terminal displays the path /home/ccuser as output.
=> You can customize the HOME variable if needed, but in most cases this is not necessary.

- $ echo $PATH

/home/ccuser/.gem/ruby/2.0.0/bin:/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin
PATH is an environment variable that stores a list of directories separated by a colon. Looking carefully, echo $PATH lists the following directories:

/home/ccuser/.gem/ruby/2.0.0/bin
/usr/local/sbin
/usr/local/bin
/usr/bin
/usr/sbin
/sbin
/bin
=> Each directory contains scripts for the command line to execute. The PATH variable simply lists which directories contain scripts.

=> For example, many commands we've learned are scripts stored in the /bin directory.

/bin/pwd
=> This is the script that is executed when you type the pwd command.

/bin/ls
=> This is the script that is executed when you type the ls command.

=> In advanced cases, you can customize the PATH variable when adding scripts of your own.

- env = The env command stands for "environment", and returns a list of the environment variables for the current user. Here, the env command returns a number of variables, including PATH, PWD, PS1, and HOME.
- env | grep PATH = is a command that displays the value of a single environment variable. Here the standard output of env is "piped" to the grep command. grep searches for the value of the variable PATH and outputs it to the terminal.

### Summary ###

The environment refers to the preferences and settings of the current user.
The nano editor is a command line text editor used to configure the environment.
~/.bash_profile is where environment settings are stored. You can edit this file with nano.
environment variables are variables that can be used across commands and programs and hold information about the environment.

export VARIABLE="Value" sets and exports an environment variable.
USER is the name of the current user.
PS1 is the command prompt.
HOME is the home directory. It is usually not customized.
PATH returns a colon separated list of file paths. It is customized in advanced cases.
env returns a list of environment variables.