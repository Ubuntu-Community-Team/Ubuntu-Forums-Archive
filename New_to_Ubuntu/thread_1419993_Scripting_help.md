---
title: "Scripting help"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2010-03-02
I'm trying to write a script that will read in all the files in a directory and run them through a program one at a time, but I have no idea how to go about doing that.  Can someone give me sort of a generic skeleton sort of script to play around with so I can learn how to do it?

---

### Post by Paddy Landau on 2010-03-02
Look at the *find* command. Specifically, look at the *-exec* option. (Go to a terminal and type *man find*.)

If the command is potentially destructive, then test your command carefully in a test directory with test files.

You can also look at the *xargs* command.

---

### Post by scared0o0rabbit on 2010-03-02
The command isn't destructive at all, it just looks at the file and spits something out as a separate file.

I'll take a look at the commands you suggested.

---

### Post by scared0o0rabbit on 2010-03-02
Okay, so I figured out how to get it to send my filenames to the command itself with the -exec command, which is working awesome, now my next question, is it possible to truncate the output of the find, so I could take the last whatever number of characters off of the output to pass to the program as another argument?

---

### Post by Paddy Landau on 2010-03-02
> **scared0o0rabbit said:**
> Okay, so I figured out how to get it to send my filenames to the command itself with the -exec command, which is working awesome, now my next question, is it possible to truncate the output of the find, so I could take the last whatever number of characters off of the output to pass to the program as another argument?
For that, I think that you'll have to write a script. (Someone correct me if I'm wrong.)

You may want to learn [gawk]("http://en.wikipedia.org/wiki/AWK") (in the repository). It's a basic script programming language for Linux, so use it only if you're a serious programmer.

It's also possible with normal bash, but I don't have a simple answer for you, sorry (I don't know bash well).

---

### Post by KiLaHuRtZ on 2010-03-02
```
ls /some/directory | while read file; do cat "${file}" | [YOUR-CMD]; done
```

---

### Post by Paddy Landau on 2010-03-02
> **KiLaHuRtZ said:**
> ```
ls /some/directory | while read file; do cat "${file}" | [YOUR-CMD]; done
```
Smart!

You could also have:
```
for file in $( ls /some/directory ); do [YOUR-CMD]; done
```where [YOUR-CMD] can use "${file}".

Example (in a script):
```
for file in $( ls /some/directory )
do
    echo "${file}"
    *etc.*
done
```

---

### Post by kaibob on 2010-03-02
> **scared0o0rabbit said:**
> Okay, so I figured out how to get it to send my filenames to the command itself with the -exec command, which is working awesome, now my next question, is it possible to truncate the output of the find, so I could take the last whatever number of characters off of the output to pass to the program as another argument?
There are a number of methods that can be used to extract characters from a string. We really need more information on your shell script and some examples of the output to answer your question. But, if you just want to do it numerically, the following works:

> $ var=123456789 ; echo ${var:(-3):3}
789

To get a better idea of this, open a terminal window, change to a directory that contains files, and enter the following:

```
for file in * ; do echo "${file:(-3):3}" ; done
```

---

### Post by scared0o0rabbit on 2010-03-03
Essentially I need a script that will allow me to run command <filename> <filename - last 4 characters>.  Hopefully that clears up what I need?

Edit: And all of the files have different length names, otherwise I think I know how I'd do it.

---

### Post by scared0o0rabbit on 2010-03-03
```

for file in $( ls /some/directory )
do
    echo "${file}"
    etc.
done

```


It seems like this is almost what I need.  If there was some way to do it as:

```

for file in $( ls /some/directory )
do
    echo "${file}" "${file except for the last 4 characters"
done

```

I think it'd work perfectly, except I don't know how to do that lol.  I think something like this might work too:

```

for file in * ; do echo  "${file}" "${file:(-4):-80}" ; done

```
Except the -80 thing won't work because that argument has to be positive.  Is there some way to do that?

---

### Post by asmoore82 on 2010-03-03
> **scared0o0rabbit said:**
> Essentially I need a script that will allow me to run command <filename> <filename - last 4 characters>.  Hopefully that clears up what I need?

Edit: And all of the files have different length names, otherwise I think I know how I'd do it.

It doesn't make any sense at all that a command would require arguments like
this, any command given <filename> could figure out <filename - 4> on its own.

What if a filename has less that 4 characters to begin with??
Are you just trying to remove the extension from the filename??

I'm not sure if you are being intentionally vague about this mystery command or not;
But perhaps you should tell us what your real goal is...
it's more than likely that there is a better way to go about it altogether.

I'd love to help as much as I can.

The most important thing to know to start out with is *_don't_* do this:
```
[COLOR="Red"]#avoid this
ls /some/dir | commands

#and avoid this
find /some/dir -type f | commands

#and really avoid this
for file in $( ls /some/dir ); do commands[/COLOR]
```
^the reason to _*not*_ do any of the above is because they cannot handle
filenames with special characters in them, even not-so-special characters
such as spaces will break most of them.

there are only 2 choices for the proper way to proceed:

1. the combination of `find` and `-print0` with `xargs` and `-0`
```
[COLOR="Blue"]#much better[/COLOR]
find /some/dir -type f [COLOR="Blue"]-print0[/COLOR] | xargs [COLOR="Blue"]-0[/COLOR] commands
```
2. the wildcard `*' with a `for` loop
```
[COLOR="Blue"]#probably the best[/COLOR]
for file in /some/dir/*
do
   commands
done
```
^this will almost always be the best possible solution,
with the wildcard `*' *_The Shell_* does the expansion for you
and hence handles all of the special characters properly.

---

### Post by scared0o0rabbit on 2010-03-03
Well actually yes I am trying to remove an extension lol.

Essentially the program takes the file and tries to expand it into a directory.  The first argument is the file, and the second is a directory name that may or may not exist yet.  I'm trying to find a way to have the second argument be automatically generated from the filename that I'm finding for the first argument.  I could do it one file at a time by typing it all manually, but I'd rather be able to do it automated.

Hopefully that clears up what I'm trying to do.  So far I've managed to get the first argument into the command, but I haven't been able to figure out how to do the second portion.

---

### Post by scared0o0rabbit on 2010-03-03
> **asmoore82 said:**
> 
there are only 2 choices for the proper way to proceed:

1. the combination of `find` and `-print0` with `xargs` and `-0`
```
[COLOR="Blue"]#much better[/COLOR]
find /some/dir -type f | xargs -0 commands
```
2. the wildcard `*' with a `for` loop
```
[COLOR="Blue"]#probably the best[/COLOR]
for file in /some/dir/*
do
   commands
done
```
^this will almost always be the best possible solution,
with the wildcard `*' *_The Shell_* does the expansion for you
and hence handles all of the special characters properly.

So if I understand what that second one is doing it is:

Getting a filename and storing it in a variable named file and then I can do commands in the loop with the file variable, so I could in essence do a:

```

for file in /some/dir/*
do
   someCommand file <second argument>
done
```

but that still leaves me with the problem of figuring out how to automatically generate the second argument based upon what's stored in file.

---

### Post by Paddy Landau on 2010-03-04
OK, here's a script that would do it for you. Save it as a file (and remember to give the file execute privilege). Please test it carefully in a copy of the directory, in case there is some bug. I have **not** tested it as I haven't the time. And thanks to kaibob for the neater loop.
```
#!/bin/bash

# Go to your directory.
cd *yourdirectory*
if [[ ${?} != 0 ]]   *# If the command failed.*
then
    echo 'Failed to change to directory.'
    exit
fi

*# Run for each file in the directory.*
for FILE in *
do
    *# Ignore if it's not a normal file (e.g. if it's a directory).*
    if [[ -f "${FILE}" ]]
    then
       * # Find the name excluding the extension.*
        DIRNAME=${DIRNAME%.*}    *# This removes the trailing .**
        *# Create the directory only if it doesn't already exist.*
        if [[ ! -d "${DIRNAME}" ]]
        then
            mkdir "${DIRNAME}"    *# Create the directory.*
            if [[ ${?} != 0 ]]
            then
                echo "Failed to create directory ${DIRNAME}"
                exit
            fi
            *# Here, do whatever you need to do after creating the directory.*
        fi
        *# Here, do whatever else you need to do with the file and directory.*
    fi
done
```

---

### Post by nothingspecial on 2010-03-04
> **scared0o0rabbit said:**
> Well actually yes I am trying to remove an extension ```


 for i in `(find . -name "*[COLOR="Red"].mp3[/COLOR]")`; do mv $i ${i/[COLOR="Red"].mp3[/COLOR]/}; done
```

This will remove the .mp3 extension in the working directory [SIZE="3"]**and all subdirectories**[/SIZE].

Change the .mp3 for the extension you want to remove.

Test the command, for example if you issue this from / you will remove the .mp3 extension from every mp3 file on the entire computer including mounted external drives etc.

---

### Post by Paddy Landau on 2010-03-04
> **nothingspecial said:**
> for i in `(find . -name "*[COLOR=Red].mp3[/COLOR]")`;
That's a good point. In my code, change the first line of the loop from
[FONT=Courier New]for FILE in *[/FONT]
to
[FONT=Courier New]for FILE in *.*
[/FONT]
I don't quite know what you mean by "expand [the file] into a directory"; I'm guessing you have a series of archives that you want to extract.

---

### Post by scared0o0rabbit on 2010-03-04
I essentially have now what I need to do it a directory at a time with the following code:

```

#!/bin/bash



# Run for each file in the directory.
for FILE in *.*
do
    # Ignore if it's not a normal file (e.g. if it's a directory).
    if [[ -f "${FILE}" ]]
    then
        # Find the name excluding the extension.
        DIRNAME=${FILE%.*}    # This removes the trailing .*
        # Create the directory only if it doesn't already exist.
        if [[ ! -d "${DIRNAME}" ]]
        then
            mkdir "${DIRNAME}"    # Create the directory.
            if [[ ${?} != 0 ]]
            then
                echo "Failed to create directory ${DIRNAME}"
                exit
            fi
            # Here, do whatever you need to do after creating the directory.
        fi
        # Here, do whatever else you need to do with the file and directory.
	echo "${FILE}" "${DIRNAME}"
    fi
done

```

Now the only other question I have is if there's a way to have it traverse sub directories also?  It's very similar to the script you posted above as you can no doubt tell, but I noticed you were trying to create DIRNAME from DIRNAME instead of file lol.  It slipped my notice the first several times I tried to get it working.

---

### Post by asmoore82 on 2010-03-04
> **nothingspecial said:**
> ```


 for i in `(find . -name "*[COLOR="Red"].mp3[/COLOR]")`; do mv $i ${i/[COLOR="Red"].mp3[/COLOR]/}; done
```

This will remove the .mp3 extension in the working directory [SIZE="3"]**and all subdirectories**[/SIZE].
...

Once again, **_[COLOR="Red"][SIZE="3"]Avoid this at all costs!![/SIZE][/COLOR]_**
It breaks for filenames with spaces or other IFS characters in them.

P.S. I edited my earlier post because I forgot the `-print0` with `find`.

---

### Post by Paddy Landau on 2010-03-04
> **scared0o0rabbit said:**
> I noticed you were trying to create DIRNAME from DIRNAME instead of file lol.
Well spotted. I did warn you that I hadn't tested it!
> **scared0o0rabbit said:**
> Now the only other question I have is if there's a way to have it traverse sub directories also?
That will require some careful programming. Create a [FONT=Courier New]function[/FONT] to do the work. Then, have the function treat directories differently; let it call itself (recursively) whenever it hits a directory.

I've slapped up a program, but, again, I haven't tested it at all. You'll have to test and debug. Note how I had to revert the first line of the loop to the original version.
```
#!/bin/bash

# Function to traverse a single directory. It will call itself recursively.
# It assumes that you are already in the right directory.
function traverseDirectory
{
    # Run for each file in the directory.
    for FILE in *
    do
        # Directory, file or other?
        if [[ -d "${FILE}" ]]
        then
        # A directory. Recursively traverse it.
            pushd "${FILE}" >/dev/null    # Change to the directory and remember it.
            if [[ ${?} != 0 ]]
            then
                echo "Failed to change directory to ${FILE} in ${PWD}"
                exit
            fi
            traverseDirectory    # Recursively traverse the subdirectory.
            popd >/dev/null      # Return to the previous directory.
            if [[ ${?} != 0 ]]
            then
                echo "Failed to return to higher level from ${FILE} in ${PWD}"
                exit
            fi
        elif [[ -f "${FILE}" ]]
        then
        # A file. Process it.
            DIRNAME=${FILE%.*}    # Removes the trailing .*
            if [[ "${DIRNAME}" == "${FILE}" || -z "${FILE}" ]]
            then
                echo "Found a file without an extension: ${FILE} in ${PWD}"
                exit
            fi
            # Create the directory only if it doesn't already exist.
            if [[ ! -d "${DIRNAME}" ]]
            then
                mkdir "${DIRNAME}"    # Create the directory.
                if [[ ${?} != 0 ]]
                then
                    echo "Failed to create directory ${DIRNAME} in ${PWD}"
                    exit
                fi
            fi
            echo "${PWD}/${FILE} ${DIRNAME}"
        fi
    done
} # traverseDirectory

# Start.
read -n 1 -p "About to traverse ${PWD}. Continue? " ANSWER
echo
if [[ "${ANSWER}" == 'y' ]]
then
    traverseDirectory
else
    echo 'Terminated.'
fi
```I'm hoping that some clever person will show me a more elegant way to do it!

---

### Post by asmoore82 on 2010-03-04
> **scared0o0rabbit said:**
> Well actually yes I am trying to remove an extension lol.

Essentially the program takes the file and tries to expand it into a directory.  The first argument is the file, and the second is a directory name that may or may not exist yet.  I'm trying to find a way to have the second argument be automatically generated from the filename that I'm finding for the first argument.  I could do it one file at a time by typing it all manually, but I'd rather be able to do it automated.

Hopefully that clears up what I'm trying to do.  So far I've managed to get the first argument into the command, but I haven't been able to figure out how to do the second portion.

```
for file in *.*
do
   if [ -f "$file" ]; then
      someCommand "$file" "${file%.*}"
   fi
done
```

Things to notice:
1. *.* makes sure that you only pick up files with extensions
2. always encase variable references in quotations: "$file"
3. the BASH Shell way to remove an extension from a name is: "${file%.*}"
This works for any arbitrary length extension: .mp3, .jpeg, .torrent, etc.

---

### Post by Paddy Landau on 2010-03-04
> **nothingspecial said:**
> ```
 for i in `(find . -name "*[COLOR=Red].mp3[/COLOR]")`; do mv $i ${i/[COLOR=Red].mp3[/COLOR]/}; done
```
> **asmoore82 said:**
> Once again, Avoid this at all costs! It breaks for filenames with spaces or other IFS characters in them.
To solve that problem, use both quotes and, instead of a pipe, -execdir.
```
find . -name '*.*' -execdir mv "{}" "$\{{}%.*}" ;
```Warning: I've not tested this.

(This is for instruction only, as it doesn't do what the OP wanted.)

---

### Post by asmoore82 on 2010-03-04
this was surprisingly easy... complex, but easy...
```
function recurse ( )
{
   if [ -z "$1" ]; then
      recurse .
      return
   fi

   if [ -f "$1" ]; then
      echo "$1"
      return
   fi

   if [ -d "$1" ]; then
      for dirs in "$1"/*
      do
         recurse "$dirs"
      done
      return
   fi
}
```^^needs a lot of testing and vetting, replace the `echo` statement with commands as needed

The only good, robust `find` solution would be like this:
```
function mycommand ( )
{
   for arg in "$@"
   do
      if [ -f "$arg" ]; then
         echo command "$1" "${1%.*}"
      fi
   done
}

find /some/dir -iname "*.*" -print0 | xargs -0 mycommand
```
^again, replace `echo` as needed

---

### Post by asmoore82 on 2010-03-04
> **Paddy Landau said:**
> 
```
find . -name '*.*' -execdir mv "{}" "$\{{}%.*}" ;
```

this doesn't even make sense, you are attempting to make find perform Shell style
variable expansion "${file%.*}" on something that isn't even a Shell variable.

needless to say, I tested it and it doesn't work *_at all_*
```
**[COLOR="Blue"]$[/COLOR]** ls
listing  text file.txt  trick;file
**[COLOR="Blue"]$[/COLOR]** find . -type f -execdir echo "{}" "$\{{}%.*}" \;
./trick;file $\{./trick;file%.*}
./text file.txt $\{./text file.txt%.*}
./listing $\{./listing%.*}
```

But all is not lost, one could hybrid our 2 solutions:
```
function mycommand ( )
{
   #given nothing, do nothing
   [ -z "$1" ] && return

   if [ -f "$1" ]; then
      echo command "$1" "${1%.*}"
   fi
}

find /some/dir -name "*.*" -exec mycommand {} \; 
```
The other `find` and `-print0` solution above will still be more efficient,
^^This one spawns a whole new `mycommand` process for each file it finds.

---

### Post by nothingspecial on 2010-03-04
> **asmoore82 said:**
> 
It breaks for filenames with spaces or other IFS characters in them.


Depends on what you are doing, what you know, what you don`t know, what you`ve done and what you are trying to do .......... but point taken.

---

### Post by asmoore82 on 2010-03-04
Late breaking news!!
neither `find` solution works because neither `find` nor `xargs` can call a shell function,
they will work if you make the function a standalone shell script.

the recurse() function is still solid gold though, until proven otherwise :razz:

---

### Post by scared0o0rabbit on 2010-03-04
This does almost exactly what I was going for, though it doesn't seem to actually do anything in the directory it's run from.  I'm going to try it with a few more sub directories of depth to see if it will continue to work, and I think I know how to modify it to work in the directory it's run from also.

```
#!/bin/bash

# Function to traverse a single directory. It will call itself recursively.
# It assumes that you are already in the right directory.
function traverseDirectory
{
    # Run for each file in the directory.
    for FILE in *
    do
        # Directory, file or other?
        if [[ -d "${FILE}" ]]
        then
        # A directory. Recursively traverse it.
            pushd "${FILE}" >/dev/null    # Change to the directory and remember it.
            if [[ ${?} != 0 ]]
            then
                echo "Failed to change directory to ${FILE} in ${PWD}"
                exit
            fi
            traverseDirectory    # Recursively traverse the subdirectory.
            popd >/dev/null      # Return to the previous directory.
            if [[ ${?} != 0 ]]
            then
                echo "Failed to return to higher level from ${FILE} in ${PWD}"
                exit
            fi
        elif [[ -f "${FILE}" ]]
        then
        # A file. Process it.
            DIRNAME=${FILE%.*}    # Removes the trailing .*
            if [[ "${DIRNAME}" == "${FILE}" || -z "${FILE}" ]]
            then
                echo "Found a file without an extension: ${FILE} in ${PWD}"
                exit
            fi
            # Create the directory only if it doesn't already exist.
            if [[ ! -d "${DIRNAME}" ]]
            then
                mkdir "${DIRNAME}"    # Create the directory.
                if [[ ${?} != 0 ]]
                then
                    echo "Failed to create directory ${DIRNAME} in ${PWD}"
                    exit
                fi
            fi
            echo "${PWD}/${FILE} ${DIRNAME}"
        fi
    done
} # traverseDirectory

# Start.
read -n 1 -p "About to traverse ${PWD}. Continue? " ANSWER
echo
if [[ "${ANSWER}" == 'y' ]]
then
    traverseDirectory
else
    echo 'Terminated.'
fi
```

---

### Post by scared0o0rabbit on 2010-03-04
Okay, a closer look reveals that it only traversed the first sub-directory and then didn't go into any of the others.

This seems like this is getting rather confusing, perhaps I'll just go back to one that works in the current directory and just run it manually in each sub directory...

---

### Post by Paddy Landau on 2010-03-05
> **asmoore82 said:**
> this doesn't even make sense, you are attempting to make find perform Shell style...
...
neither `find` solution works because neither `find` nor `xargs` can call a shell function,
they will work if you make the function a standalone shell script.
Thanks for the extra info. I'm always learning!

> **scared0o0rabbit said:**
> Okay, a closer look reveals that it only traversed the first sub-directory and then didn't go into any of the others.
Puzzling. I just did a test and it worked for me. :confused:

> **scared0o0rabbit said:**
> This seems like this is getting rather confusing, perhaps I'll just go back to one that works in the current directory and just run it manually in each sub directory...
Sometimes, the KISS principle works best!

---

