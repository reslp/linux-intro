# Introduction to Linux and working on the command line

**Contents**

**1 First steps**   
  - [1.1 A brief history of Unix and Linux](#a-brief-history-of-unix-and-linux)  
  - [1.2 What is the Linux shell?](#what-is-the-linux-shell)  
  - [1.3 Basic concepts and definitions](#basic-concepts-and-definitions)  
  - [1.4 Connecting to remote computers](#connecting-to-remote-computers)  

**2 Basic commands**  
  - [2.1 Navigating the file system](#navigating-the-file-system)  
  - [2.2 Editing, inspecting, and searching within text files](#editing-inspecting-and-searching-within-text-files)  
  - [2.3 Search, replace, and write output to a new file](#search-replace-and-write-output-to-a-new-file)  
  - [2.4 Combining multiple commands into scripts](#combining-multiple-commands-into-scripts)  

**[3 Additional reading](#additional-reading)**

# 0 Learning goals

- Today we will learn how to work in command-line interaces of Unix based systems.
- We will teach you the basics of navigating the file system, viewing and searching large data files.
- You will also learn to chain commands together to make your work quicker and more reproducible.
- We will introduce ways on how to think about your data analysis with powerful command line tools. 

**A great way to learn and extend your knowledge about the command line is to search online for instructions and then try them yourself, experimenting as much as you can.**

The computer is our lab and we want to use it as efficiently as possible.

# 1 First steps

## 1.1 A brief history of Unix and Linux

Unix is an operating system first developed in the late 1960s at AT&T's Bell Labs by [Ken Thompson](https://en.wikipedia.org/wiki/Ken_Thompson), [Dennis Ritchie](https://en.wikipedia.org/wiki/Dennis_Ritchie), and others. It was designed to be portable (could be adapted quickly to different hardware), multi-tasking (can run multiple tasks simultaneously), and multi-user (yould be used by multiple people at the same time). Unix was written in a high-level programming language ([C](https://en.wikipedia.org/wiki/C_(programming_language))) which was a revolutionary concept at the time as, until then, operating systems were usually written in [assembly](https://en.wikipedia.org/wiki/Assembly_language) language. This made Unix easy to modify, expand, and port to other machines.

Linux is a Unix-like operating system that came into existence in the early 1990s when a Finnish student, [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds), started a project to create a new free operating system kernel. Unix variants at the time were all proprietary. Torvalds released the initial code on the internet and invited others to contribute. This collaborative, open-source approach allowed Linux to grow rapidly.

Linux is based on the principles and design of Unix however it is built from scratch by a community of developers worldwide, led by Torvalds. It is free to use and distribute, which has led to its widespread use across personal computers, servers, mobile devices, and more. Over time, groups of developers have packaged the Linux kernel with a variety of software to create complete operating systems, known as distributions (distros), like Ubuntu, Fedora, and Debian.

The similarities between Unix and Linux boil down to their shared design philosophies, use of a common command-line interface (CLI), and similar system architecture. However, they differ in their licensing, with Unix often being proprietary and Linux being free and open-source. Both operating systems have had a profound impact on the computing landscape, influencing the development of various systems and applications that we use today.


## 1.2 What is the Linux shell?

The Linux shell,  allows users to interact with the computer's operating system through text commands also refered to as a command-line interface (CLI). This might seem daunting to novices initially, especially in an era dominated by graphical user interfaces (GUIs) with mouse control. However, the shell is a powerful tool that offers precision, control, and a deeper understanding of how computers work. In its essence it is a programm expecting and executing commands, but it can alsoalso  do a lot more than that. 

The Unix operating system, the progenitor to Linux (see above), came with its own shell, the Bourne shell. With time, various other shells were developed, but the most popular in the Linux world is called `Bash`, which stands for 'Bourne Again SHell.' Bash is an enhanced version of the original Bourne shell, incorporating new features and improvements to make it more usable and powerful.

Why use the Linux shell? For starters, it's incredibly efficient for repetitive tasks. Complex operations that might require lots of dragging and clicking in a GUI can often be done with a single command. The shell also excels in scriptability; users can write scripts (essentially a list of commands) to automate a wide array of tasks.

The power of the shell comes from its ability to harness the capabilities of the Linux operating system, where even the most fundamental aspects like file management and software installation can be controlled with precision through shell commands. While graphical interfaces provide a user-friendly layer on top, the real machinery that performs the heavy lifting works under those graphical programs, is accessible almost  exclusively through the shell.

Learning to use the Linux shell can seem like learning a new language — because it is. But just as knowing the basics of a language helps in a foreign country, knowing basic shell commands is incredibly beneficial to navigate and utilize the full potential of Linux-based systems. As we make our first steps into this world, after a little practice, we will gain a level of control and efficiency never imagined possible.

## 1.3 Basic concepts and definitions

This introduction includes a large number of examples.
The \$ symbol in the examples below indicates what is called the [*command prompt*](https://en.wikipedia.org/wiki/Command-line_interface#Command_prompt), rather
than something you type. This may, on some systems be prefixed with additional text, or be formatted differently.\
You will see something like `symbiont@lichengenomics:\~\$` which refers to the user you are
logged in as, before the @ symbol, the name of the computer you are
using and the current directory, after the : symbol. The tilde \~
signifies your home directory (more on that in section 2.1 below).

To execute commands in the shell you type your command and hit "Enter"
(Return) to execute the command. The output will appear in the same
window below the command prompt.

The exercises are split into sections of text with explanations of what we are doing and so-called code blocks which contain the actual commands we will be running:

```
# This is an example code block. Typically you can copy and paste what is here and execute it by pressing <Return>.
```

## 1.2 Connecting to remote computers

### Theory: What is SSH?

SSH, or Secure Shell, is a network protocol that allows you to securely access a computer over an unsecured network. Imagine you're in your home, and you want to send a secret message to a friend in a house across the street. Rather than shouting the message out loud where anyone could hear, you use a special secure tunnel that only you and your friend can use. This is what SSH does for computers.

When you use SSH, it's like creating a secure tunnel for your data. You can run commands on a remote computer as if you were sitting right in front of it, even if it's on the other side of the world. This is particularly useful for large-scale data analysis, performing techical tasks, or transferring files securely. To connect to a remote computer with SSH, all you need is the SSH software on your own computer, the remote computer's address, and the appropriate access permissions. With these essentials, SSH ensures that your connection and data stay encrypted and safe from eavesdroppers.

Since we will be analyzing very large datasets, our own laptops and desktop computers typically do not have enought memory or CPU power. Hence we will be working on 
the University of Graz High-Performance Compute Cluster - [GSC](https://hpc-wiki.uni-graz.at/) which we access through SSH. Using our UGO Account and passwords you should be able to log in.
Open a terminal window on your system and type:

```
$ ssh <username>@gsc.uni-graz.at
<omitted long output here>
----------------------------------------------------------------------------------
Last login: Fri Apr  4 13:29:38 2025 from 142.55.237.189
username@IT010044: ~ $ 
```

Congrats, you have successfully executed your first command line program which should log you in to the Uni Graz cluster. Mind you that this only works from inside the University network or through a VPN connection.

# 2 Basic commands

> [!IMPORTANT]
> Before you proceed type (or copy-paste) the following text into your shell and hit Return (Enter). This will automatically download the input data for this course.
> We will discuss later what exactly this command is doing:
>
> ```
> $ git clone https://github.com/reslp/linux-intro.git
> ```


## 2.1 Navigating the file system

Once logged in, the first thing to do is to learn the basics of moving between
directories on your computer, checking where you are, checking what
files are present and having a quick look at them. Some of the
terminology is perhaps slightly new (*directories* rather than
*folders*) but using the right words will mean you are speaking the same
language as everyone else and make your life easier when Googling for
solutions.

### 2.1.1 See where you are and how to move between directories

At the command line you need to know "where you are" i.e. which
directory you have open and are working in. Question: If you
issue the command to 'list all files' which files will be listed?
Answer: Those in the folder where you are currently working, called the
[working directory]{.underline}. 

The command to find out where you are
is `pwd` short for *print working directory*. 

*print* when working at the command line
means *display on the screen* rather than *write this to a piece of
paper or a file*.

Type the command to display your current directory now (and hit Enter)

You should see something like this, with your command on the line
beginning with the \$ prompt and the output on the line below

```
$ pwd
/usr/people/EDVZ/username
```

But maybe that isn't where you want to be, in which case you need to
'[c]{.underline}hange [d]{.underline}irectory' and the command for that
is cd.

```
$ cd genomics_course
$ cd data
$ pwd
/home/symbiont/genomics_course/data
```

You can see that the / symbol denotes levels of directories, so that
`data` directory is contained within the `genomics_course` directory
which is within the `symbiont` user home directory in the system's
`home` directory. These *file paths* can be long sometimes but they are
always explicit, which is a very good thing for reproducibility. There
is no excuse for trying to remember where the data was stored for your
analysis, here it is written out, and you will want to record this as
part of your experiment.

You can go up one level (to the directory containing your current
working directory) by using double dots (ensure there is always a space
between the cd command and the directory you wish to go to).

```
$ cd ..
$ pwd
/usr/people/genomics_course/
```

What happens if you use the cd command without telling the system where
you would like to change directories to? Try it. How can you find out
which directory you are now in?

```
$ cd
$ pwd
/usr/people/username
```

Using cd command on its own returns you to your user's home directory,
in this case `/usr/people/symbiont` from wherever you are.

The tilde symbol (**\~**) is shorthand for this home directory so
`/home/symbiont/genomics_course` and `~/genomics_course` refer to the same
directory, which saves a little typing.

The exact location of your home directory will depend on the flavor of Linux/Unix you are using.
On Apple MacOS, for example, it would be something like `/Users/username`.

Another very useful shortcut is `cd -` (dash) which takes you to the
previous directory that you were in. This is really useful when you need
to swap between directories that are separated by several levels or that
have long names.

```
$ cd ~/genomics_course/data
$ pwd
/usr/people/username/genomics_course/data
$ cd
$ pwd
/usr/people/username
$ cd -
$ pwd
/usr/people/username/genomics_course/data
$ cd -
$ pwd
/usr/people/username
```

Make sure that you are actually typing this out for yourself rather than
just reading along. This *active learning* will really help it to stick
in memory, and come back when you need it, a bit like developing muscle
memory.

Above we were issuing commands one at a time; first `cd` then `pwd`. To
chain commands together on the same line separate them with a semicolon
ie `cd;pwd`.

Try the exercise above again but using semicolons. You should now only
need 4 commands not 8.

One of the underlying principles of UNIX type operating systems is that
every item should do one thing (and one thing only, but this very well) and that we can
easily join these items together (usually with `;` or a pipe `|` described
later). Think of it like a set of lego blocks that we may put together
however we like to build anything we want. Simple units, building
complex and impressive outcomes.

We have prepared example data to be used in the following exercises in a
directory on your computer - `EXAMPLE DATA PATH`.

Navigate to this directory and then confirm that you are in the right
place by printing the working directory path to your screen. Then go
back to your home directory before returning to the directory above
again to practice your new skills. Test yourself first, but it's OK to
review different ways to do this again from the manual above. Looking
things up is not cheating.

#### 2.1.1.1 Ways to return home

There are 5 ways that you should now know to return to your home
directory. Try each to show that they work and discuss with others, 
most people only get 2 or 3.

<details>
  <summary>Solution: Five ways to return home</summary>

  ```
  $ cd /usr/people/username
  $ cd 
  $ cd ~
  $ cd ..;cd ..
  $ cd -
  ```
</details>

### 2.1.2 Listing the contents of a directory with ls

A very common thing you will want to do is to display the contents of a
directory, i.e. list all the files. You can list the files (and
directories) in your working directory using the ls command. For this
exercise we will be using the raw data folder.

>[!CAUTION]
>Spaces in file and directory names cause difficulties as the shell
treats spaces as the end of a file name. When looking for `my file` it
complains that it can't find `my`.

Look here:
```
$ cd my directory
-bash: cd: my: No such file or directory
```

Although this can be got around by using quotes `cd 'my file'` replacing
with underscores (e.g. `my_file`), hyphens (e.g. `my-file`), or
concatenating the words (e.g. `myfile`) are usually better ways to work.

```
$ ls
```

Try listing files in long format.

>[!TIP]
>You can Google to find out what all the data listed means, or better use the built in manual (`man`) pages.

```
$ man ls
```

Hit the spacebar to advance through the pages. Typing q (quit) will get
you out of a man page. You can use man with any command, not just `ls`.

```
$ man man
```

**Googling is not cheating**, it is a great way to learn and is highly
recommended.

ADD SMALL NAVIGATION EXERCISE

How would you do this on a single line command? Show that it works

### 2.1.3 Some things you will have noticed 

Firstly, you have to type very carefully, any typo and you
will get an error that the file or directory doesn't exist, e.g:

```
$ cd dayy-1
bash: cd: dayy-1: No such file or directory
```

A second thing you will have noticed is that some file
names are long, complex, and difficult to type without errors.

>[!TIP] 
>You need to learn to use the *tab* key to autocomplete names.

Real command line gurus use the tab key extensively. If you start typing
the command and then hit tab the filename will be auto completed, or, if
you haven't typed enough yet to specify a single file (it could be one
of several beginning with the same letters) you will probably get a
beep, followed by a list of files or directories beginning with those
letters. It will also autocomplete the portion of the file or directory
name that is shared between them all and wait for you to type more and
hit tab again.

Try it now. Navigate to `genomics_course/raw_data/` and list the files
present. You should have explored using tab to autocomplete the
directory names at every level. If not quickly jump back using `cd -` and
try again.

## 2.2 Editing, inspecting, and searching within text files

### 2.2.1 Editing files

UNIX based systems provide several powerful utilities for editing and
inspecting files, either from the command line, or in a simple graphical
user interface. You can use the gedit program in Linux to open files for
viewing and editing in a graphical way, much like **Notepad** or
**TextWrangler** in Windows or OSX. Don't start doing this though, it
has limitations and is a waste of your time on this course, learn the
command line instead. Here we will use the simple text editor nano there
are many others beyond the scope of this tutorial. The strength of nano
lies in its simplicity. Help: [a beginners guide to nano](http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/)

To view our **scaffold.fas** file in nano you should use the general
unix approach of program-name filename, and assuming we are still in the
**day-1** directory:

```
$ nano scaffold.fas
```

Did you tab complete the name? If not exit using Ctrl+X and try again.
*Reinforce your skills*

**TASK**: To practice nano rename the sequence to `>fungal_scaffold` save
the changes using Ctrl-O (called writing-**O**ut), it will ask you if
you want to save to the same file, don't, give a new informative name
like:

```
scaffold_renamed.fas
```

>[!TIP]
>To close nano you should use the Ctrl+X key combination (see
\^X Exit in the lower left of the nano screen, where the \^ denotes the
Ctrl key). You can find [nano helppages](http://mintaka.sdsu.edu/reu/nano.html) with a Google
search. You can also use `man nano`.

To close less (below) you should just type `q`. Using Ctrl+X or q will
generally close most UNIX programs, if either of those don't work you
can also use the Ctrl+C key combination to *kill* the program and return
to the command prompt.

### 2.2.2 Inspecting files

nano allows us to edit the file *in situ*, however, if we just want to
inspect the file we can display its contents using several other UNIX
programs:

1.  `cat` to print the whole file to the screen

2.  `less` to print the file a page at a time to the screen

3.  `head` to print the first few lines of the file on screen

4.  `tail` to print the last few lines of the file on screen

One of the problems with DNA sequence files is that they can be large -
several hundred megabytes to a few gigabytes is not uncommon. Viewing
these files can be difficult, as the files need to be loaded into
memory, and can therefore take a great deal of time for the text editor
to read from the disk. The `less`, `head` and `tail` commands are very
efficient for viewing large files such as these.

**TASK:** All these commands will be useful for you during this course.
You should now try using less, head, tail and cat to practice seeing the
text file `parmelia_sequences.fas` which can be found in
`~/raw_data/fasta/`. Are you using ls to see what is available and tab to
complete the filename? How can you step through the file a screen at a
time using less? Try Googling for the answer and demonstrate that it
works.

### 2.2.3 Searching within files

**Searching** within very large files however can be even more
troublesome, especially using the standard find functions in a text
editor, which aren't optimised for performing searches across very large
files. For this reason various tools have been created that allow users
to search within large files from the command line, and are highly
optimised for their function. One of the most useful utilities for
searching within a file is `grep` (**g**lobal **r**egular **e**xpression
**p**arser).

`grep` is very simple to use. At the command line you will need to type
the word grep, followed by the text you are searching for, followed by
where (the filename) to look for it. For example, to search for the word
RPB1in our `parmelia_sequences.fas` file we do the following:

```
$ grep "RPB1" 18S_parmelia_sequences.fas
```
This returns all the lines containing the word *RPB1*.

We can count how many of the sequences are RPB1 by using the *count*
flag (`-c`) with `grep` as follows:

```
$ grep --c "RPB1" 18S_parmelia_sequences.fas
```

### 2.2.4 How many sequences do I have?

A very common question to ask is:  *how many sequence records are in
this enormous fasta file?*

>[!NOTE]
>FASTA files are a common text-based files to store nucleotide and amino acid sequences. Look [here](https://en.wikipedia.org/wiki/FASTA_format) for more details. 
 
You could of course search for all the
greater than `>` symbols, which is almost certainly the number of
records. However you should really search for all the lines **starting
with `>`** rather than the number of times it occurs, as [it is possible
for a fasta header to contain an internal \>](https://nsaunders.wordpress.com/2014/08/14/looking-for-in-all-the-wrong-places/)
. 'Line starts with' is represented by the \^ symbol.

### Task

Try to write a grep search to count the number of fasta header
lines. Google/ask for help. **Have you remembered the quotation marks
around the search phrase?** Unfortunately your solution will probably
delete the data file if you forget the quote marks! Why? Discuss

Search the two files `scaffold.fas` and `parmelia_sequences.fas` you have
already used to determine the number of sequence records. Make sure to
discuss your solution.

>[!TIP]
>you can use the up and down arrows to cycle through your
>command history. If you find yourself typing the same command then try
>pressing the up arrow until you reach the command you want. You can
>always edit that command if you need to, perhaps using tab to
>autocomplete a new file name. Use the down arrow to bring back more
>recent commands, and eventually the command line will clear completely,
>i.e. you are back to the present 'no command'. Type history to see a
>list of all your previous commands or Ctrl-R to search them.

## 2.3 Search, replace, and write output to a new file

grep is an excellent tool for undertaking simple yet fast searches
within text files. But to search [and replace]{.underline} within a text
file, or to redirect changes to a new file, we will need to use either
sed or a simple script (OK there are actually numerous ways of doing
this utilizing other tools but this manual will only deal with *simple*
examples with sed or python scripts).

### 2.3.1 sed the stream editor

`sed` works best when we need to deal with files as single lines, or rows
of text data. Since sed doesn't try to take the whole file into memory,
instead dealing with a line at a time, it has real advantages when files
are enormous- as they often are for sequence data.

To search for and replace `RPB1` with `RPB_1` in our
`parmelia_sequences.fas` file we could do the following:

```
$ sed 's/RPB1/RPB_1/' < parmelia_sequences.fas > RPB1toRPB_1.fas
```

This will replace the single word `RPB1` we identified using grep with
the word `RPB_1`, but output these changes to the file
`RPB1toRPB_1.fas`, leaving the original file unchanged. The s within
the single quotes signifies this is a *substitution* command
and the / characters are delimiters that separate the text to search
for, and the text to replace it with. In UNIX based systems the \<
signifies an input, so we are taking input from our
`parmelia_sequences.fas` file and outputting (\>) to
`RPB1toRPB_1.fas`.

 Always give meaningful names to files and directories, even if that
makes them seem long. The person you are doing this for is 'future you'
who will remember less than you think, need clear filenames as one of
the ways to make sense of the data, how it has been transformed, and to
help record a reproducible experiment. It is very useful to have a
filename like:

```
whitby-FDS12763-nematode18S-lenfiltered200bp-uniquespecies.fas
```
instead of

```
sequences_2.fas
```

Another reason the information-in-filename approach is very useful is
that it contains a lot of information you can use for analysis. If you
had 1000 files from separate sampling points, you could choose which
files to pull data from based on names like "whitby" or "FDS". If you
wanted to grab data just from enoplid nematodes from only the Whitby
samples you could find and list (con*cat*enate) those
with a search, and pipes \| to string several jobs together. Below is an
example, these files don't exist here, but you are going to try it
yourself on files that do.

```
cat ~/allsamples/*whitby*.fas | grep enoplida | sort | uniq -c
```


### Task

Google, discuss, and ask until you know what this command
does. To help your searches the asterisks are called 'unix wildcards'
-why are they used? Think for a moment how much work this single line is
actually doing and how long it would take manually?

Above I suggested using the filename

```
whitby-FDS12763-nematode18S-lenfiltered200bp-uniquespecies.fas
```

It may seem an annoying amount of typing to write this much information
in filenames, but it isn't *you* who should be doing the writing, it's
your script. It is a difficult mindset to overcome, but really useful.

### Task

Go to the headers directory. Extract all the header lines from
headers-test.fas and write to a new file with an informative name. How
many are there? Are there any duplicates or are they all unique (uniq)?
Now repeat this for all the headers containing 2 separate search terms
(eg taxon names) that you think of. It doesn't matter what they are. You
can examine the headers in the file with your new unix skills to get
inspiration. Extra points if you can do this in one single command.
[[Answer]](https://docs.google.com/document/d/1h9d0JrTsDLzsOV5klMkD47807dWTmcXN3uxoYp0ei64/edit#heading=h.zh5kap4uuux6)


### 2.3.2 echo

A useful way to write to a text file is with echo. This will print to
the screen or a file. Here is a [short
introduction](http://www.computerhope.com/unix/uecho.htm)
to echo if you need it, although the next sections are fairly self
explanatory without it.

>[!TIP]
> Or use `man echo`

Try these commands

```
$ echo Hello world!
$ echo 'Hello world!' > greeting.txt
```

If the file `greeting.txt` does not exist it will be created. If it does
exist it will be overwritten. Check the file now exists (how?), then you
can use one of the commands above (cat maybe? Do you remember the
others?) to inspect the file you have just created. If you wish to
append text to a file rather than replace it you can use the \>\>
symbol:

```
$ echo 'Hello again world!' >> greeting.txt
```
Try this and check your success. Routing syntax (\>, \>\>) is general to
UNIX and can be used with other programs too. Imagine that you need to
add an extra fasta sequence to the end of a big sequence file, the
append symbol \>\> will be helpful. Do you remember that \< determined
the input source? Can you think of any situations in your work where
this UNIX command line approach could save an enormous amount of work in
manipulating files?

`echo` also allows us to format files correctly if we need newlines or
tabs inserted by using the `-e` flag. The tab symbol is \\t and newline
\\n.

Can you use these to better format `greeting.txt`?

Try to imagine what the following command will write & discuss with
others:

```
$ echo -e "column1\tcolumn2\nRNA\tDNA" > rna-dna-columns.txt
```


Check your success. These commands are useful when writing a lot of data
to a file programmatically, and when format such as having a defined
number of columns or lines is important, which is a *very*
common situation for bioinformatics work.  
**Remember this example.**   
You will use echo to create one of these files tomorrow.  

A common bioinformatics task is to concatenate a lot of individual
sequence files into one single file. This is very time consuming to do
in a GUI if you have more than a couple of files to open, copy, close,
open, paste. The task at the command line however *scales* easily from
1 to 1 million files. You already have all the skills to do this.


### Task

Go to the day-1/fasta-to-combine directory. Concatenate all 10
sequence files into a new file with an informative name. Do not add the
contents of the `readme.txt` file. Demonstrate your success.

Lastly echo can write file information like file names

```
$ echo *.fas > fasta-file-names.txt
```

This would write the name of every file in the current directory with a
`.fas` extension to a file called `fasta-file-names.txt` which is often very
useful when you need to record lots of output file information.

## 2.4 Combining multiple commands into scripts

### 2.4.1 Text-processing scripts

Often you will wish to do more complex tasks of manipulating text files.
These are best done with simple scripts and most bioinformaticians would
use a python script to do these sorts of tasks. Learning python is not
part of this tutorial (even though we run many python scripts) but there
are many free online courses if you wish to improve your knowledge (e.g.
[pythonforbiologists.com](http://pythonforbiologists.com/)
Google for many, many more).

You have a file `example-rna.fas` in the
`/data/exercise-0/backtranscribe` directory which holds [fasta
format](http://drive.google.com/open?id=1SE1YxDwsLmndZX8DgBx2jq8RPk1yRb2aJOqk7cUm0Ys)
RNA sequences. You need to change these sequences to DNA. You could
search and replace U with T using sed as above (try to write this
command for yourself). Unfortunately that will change every U to a T in
the sequence headers too. Instead a simple, but much more flexible and
intelligent, python script could be used,. This has been written for you
called `RNAtoDNA.py`

### 2.4.2 Python scripts

### Task

Navigate to the correct directory and identify the python
script. Instructions are in the [Navigating the File
System](#navigating-the-file-system) section above if you
have forgotten.

Have a look at this `RNAtoDNA.py` file using your new command line skills
(see above if you have forgotten). If you don't understand everything, that's OK.
Have a quick guess what some parts might mean and then read on.

Comment lines begin with a hash \# symbol. These are just for humans to
read, they are ignored when the script is executed (run). Scripts with
lots of comments are much easier to understand and you should use them
yourself when you write or modify a script.

You are already familiar with [fasta format
files](https://en.wikipedia.org/wiki/FASTA_format). Given a fasta file containing RNA sequences, how can you convert them into DNA?  
Cou could probably write some
[pseudocode](https://en.wikipedia.org/wiki/Pseudocode)
quite quickly, and one version could look like this:

-   Open the input data file containing RNA sequence

-   Create an output file with a new name to save DNA sequence to

-   If input data line starts with \> its a header line

    -   write header line to output file

    -   move on, we're not changing headers

-   Otherwise its sequence data

    -   change all U \--\> T making it a DNA sequence

    -   write changed line to output file

-   Repeat until end of file, close files, claim success

Now read the python script again, is it more understandable? Some parts
may not be obvious, but it\'s generally like the pseudocode above.
Discuss the script with someone.

### Task
Create a new DNA fasta file from the file `transcripts.fas`
provided in this directory.

In order to run a program or script we specify the program to be run
(python) and the file to be executed (`RNA2DNA.py`).

```
$ python RNA2DNA.py
```

First figure out how to run the script to produce a DNA file. Next,
google how to rename files at the unix command line, and rename the
newly created file to `new-dna.fas` or something even more informative.
NB remember spaces in filenames cause troubles at the command line,
that's why dashes or underscores are commonly used.

>[!NOTE]
>You have understood and run a python script in a unix shell, to
>reformat nucleotide sequence data. Our work here is done, you are now a
>bioinformatician, shake hands, welcome to the club!

### 2.4.3 Shell scripts- collecting together lots of commands

Similar to python scripts, the UNIX based shell allows us to execute
*shell scripts*, which usually have the .sh extension. Shell scripts
are a powerful way to link together lots of different commands and then
execute (run) them all at once. Below is a walk-through demonstrating a
shell script.

In our *day-1* directory we have a shell script: `readmap_all.sh`

Its very easy to get lost or panic in the next paragraphs. *Don't panic!*
Just skim this section and ask someone. It\'s a deliberately complex
example, the point of this exercise is not that you read in detail,
understand exactly, and remember every detail. It is to give you an idea
that

By doing a cat readmap_all.sh we can view the content of this file on
screen.

The first line (`#!/bin/bash`) is what is called the *shebang* line and
points to the location of the shell program we wish to use when
executing the program. Any other **lines that begin with a hash (#) are
comment lines** and are ignored by the shell. Comment lines can help in
describing what each part does and are therefore very useful to remind
yourself, and others, what the script was intending to do.

The first command executed is `cd trimmed_reads` which changes the
directory to `trimmed_reads`. It then immediately executes `files=$(ls renamed\_\*R1\*)`.
This lists all the files which have `renamed_*R1*` in
their filenames and saves the list of filenames to the variable named
files. The stars sign (\*) is a placeholder. It means any character(s).
Next there is another cd command which makes the script jump back to the
previous directory. The command echo "Building index file:" outputs this
message to the screen. The next line is another comment . The command
`bowtie2-build ~/data/peltigera/Peltigera_membranacea/additional_data/Pmem_fungal_scaffolds_DNA_cleaned-up/Pmem_mycobiont_scaffold_1line.fasta ./02_bowtie/Pmem_fungal_index.build` calls the program `bowtie2-build`. The
`bowtie2` software is used to [align (map)](https://en.wikipedia.org/wiki/Sequence_alignment) short sequences, usually reads
to much longer sequences such as assemblies. This process is called *read
mapping*. The purpose of this can be manifold. For example read mapping
is needed if you want to dected SNPs or look at expression level
differences in RNASeq experiments. Of course there are many other
applications for read mappping.

The line `echo "building index done"` will inform us that the index file was successfully built. The next two lines create two additional variables: `samfile_base=pmem_readmap_` and `counter=0`. The `samfile_base` variable is used as a prefix for the new file which will be created during the rest of the shell script.

You may have already guessed that this script was written to automatize readmapping for many sequenced libraries against one reference genome. The actual mapping takes place in the next few file. Since we want to do this many times we use a for loop. This loop will repeat the commands between the do and done statement for a specific number of times. In this case it is done for the number of files in the `$files` variable which we created earlier. Inside the `for` loop , the first thing which is done here is to assign several new variables containing the file paths which should be mapped. Can you guess what the `sed` command in the script does? The file names `$d` and `$d2` are then displayed on screen with `echo`. In the following line the counter variable is increase by 1: `((++counter))`. After that a new variable is defined. Can you guess what this variable may contain?

The next command calls `bowtie2` to map the reads in the read files
against the reference: `bowtie2 -p 24 -q --phred33 --fr -x ./02_bowtie/Pmem_fungal_index.build -1 $name1 -2 $name2 -S ./02_bowtie/$samfile.sam`.
 It uses many of the variables created
earlier, so hopefully now it gets more clear why we need them. The next
command is another echo command which tells us that the bowtie command
is finished. `bowtie2` creates a socalled SAM file which contains
informations about the mapped reads such as the name of the read, the
sequence and the mapping coordinates. SAM files are text format files
and you could theoretically look at them with cat although this may not
be a good idea because SAM files can get very large. This is why we have
to compress them into a compressed binary format. Compressed SAM files
are called BAM files and we compress SAM files like this: `samtools view -bS ./02_bowtie/$samfile.sam | samtools sort - ./02_bowtie/$samfile`
and work only with the compressed files. The next line only has the done
command which indicates the end of the for loop. After the loop has
finished the last few lines of code will combine all just created BAM
files into a single file sort the file and creates an index file.

#### 2.4.3.1 The point of scripts - power, speed, reproducibility

I hope you can see that this shell script has done a lot of complex work
at once. Entering all these commands with the correct flags and file
locations from the command line directly would be very difficult, error
prone and would take a lot of time especially if you have to do this
several times. **Scripts aid reproducibility and save you work.**

Imagine that you were instead in a GUI environment in Windows, and had
to click buttons and type into text boxes to change analysis parameters.
Just to set the information contained in those few lines of shell script
described above would be much more work. What if you had to repeat 3
times, changing one parameter but setting all the others the same? That
would be easy with a shell script where you already know how to search
and replace text in a text file (like a script) from the command line,
but requires a lot of repetition in a GUI. What if you had to do this
1000 times across different combinations of parameters and write
informative output filenames to record which parameters were used?
Impossible in a GUI but straightforward with only a few basic scripting
skills. You could also give the script to a collaborator to run the same
analysis on their data. Or better yet add your analysis script to the
massive number already available online for all to use without
restriction.

>[!NOTE]
>I hope you can see the reasons that bioinformaticians, and most modern
>biologists working with lots of data, use the command line and scripts
>rather than proprietary GUI programs.**

## 2.6 Tasks- review of command line skills

Use the skills you have learned to answer the questions below. The
information you need is in the sections above but this is 'open book',
you can use the internet just like a proper bioinformatician.

1.  How many `tef1` sequences are there in the `parmelia_sequences.fas`?

2.  What is the last sequence record? (No scrolling down please!)

3.  Search for `beta-tubulin` and replace it with Btub

4.  Demonstrate that you can (a) edit the file directly (b) save the
    edit as a new file

# 3 Additional reading

1.  UNIX Tutorial for Beginners
    [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

2.  Command line history tricks
    [http://www.thegeekstuff.com/2008/08/15-examples-to-master-linux-command-line-history/](http://www.thegeekstuff.com/2008/08/15-examples-to-master-linux-command-line-history/)

3.  Software Carpentry Introduction to the unix shell [on
    YouTube](https://www.youtube.com/results?search_query=software+carpentry+September+2012+unix+shell)
    (great short videos)

4.  Unix and Perl Primer for Biologists
    [http://korflab.ucdavis.edu/Unix_and_Perl/unix_and_perl_v3.0.pdf](http://korflab.ucdavis.edu/Unix_and_Perl/unix_and_perl_v3.0.pdf)

5.  Bradnam and Korf. (2012) UNIX and Perl to the Rescue!: A Field Guide
    for the Life Sciences (and Other Data-rich Pursuits). ISBN-10:
    0521169828 ISBN-13: 978-0521169820
    [http://www.amazon.co.uk/gp/product/0521169828](http://www.amazon.co.uk/gp/product/0521169828)

6.  GREP
    [http://www.gnu.org/software/grep/manual/grep.html](http://www.gnu.org/software/grep/manual/grep.html)

7.  SED
    [http://www.gnu.org/software/sed/manual/sed.html](http://www.gnu.org/software/sed/manual/sed.html)

8.  Software Carpentry Introduction to programming in Python ([great
    short YouTube videos](https://www.youtube.com/results?search_query=software+carpentry+September+2012+python))

9.  Python for Biologists
    [http://pythonforbiologists.com](http://pythonforbiologists.com)

10. Python for non-programmers
    [https://wiki.python.org/moin/BeginnersGuide/NonProgrammers](https://wiki.python.org/moin/BeginnersGuide/NonProgrammers)
