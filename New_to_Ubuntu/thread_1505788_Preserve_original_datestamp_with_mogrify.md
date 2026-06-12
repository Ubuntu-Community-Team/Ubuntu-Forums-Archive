---
title: "Preserve original datestamp with mogrify?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Zill on 2010-06-09
I must be missing something...  The following code produces new files with the current date/time when resizing whereas I wish to retain the original date/time.
```
mogrify -resize 75% *.jpg
```

How do I preserve the original date/time stamp on files that are resized with mogrify?

(or should I be using a different command? ;-) )

---

### Post by Paddy Landau on 2010-06-09
Do you mean the timestamp on the file itself, or the date & time information held within the photograph?

If the former, then of course the timestamp will change, as the file has been modified.

If you mean the latter, then sorry I don't have the answer for you.

---

### Post by Zill on 2010-06-10
Thanks Paddy.  I simply want to retain the original file timestamp after resizing to help find files in future.

I was hoping that mogrify would allow this in a similar way that "cp -p" preserves the original timestamp when copying files.

The EXIF timestamp info *does* remain unchanged after resizing but this does not really help when using a file manager.

Ideas please anyone?

---

### Post by Paddy Landau on 2010-06-10
I think you may be out of luck. In your place, I would write a script to record the timestamps, perform the mogrify, and restore the timestamps (using 'touch').

It's an unusual request. I'm curious as to why you would want to do this?

---

### Post by Zill on 2010-06-10
> **Paddy Landau said:**
> ...It's an unusual request. I'm curious as to why you would want to do this?
Thanks Paddy.  I have, for example, a directory with around 450 large jpgs in it, with dates over a 10 month period.  I need to resize all of these to make the filesizes smaller.  While I could sub-divide the jpgs into many different directories, it would be easier to leave them in one directory and then find selected ones by the original dates.  Unfortunately, mogrify will give them all the same date and almost the same time. :-(

I realise I could write a script (if I could figure it all out!) but was hoping to find a quick and easy method, preferably using a single command.

Anyone - Are there any other commands and/or short scripts that may do this?

---

### Post by Paddy Landau on 2010-06-10
I've knocked up something quick for you, Zill.

Because it's a knock-up, you need to use it most carefully as instructed. It's not idiot-proof.

[SIZE=3]**Set-up**[/SIZE]

[LIST=1]
[*]Create a directory in your home directory called [FONT=Courier New]bin[/FONT].
[*]Reboot, which will cause [FONT=Courier New]~/bin[/FONT] to be added to your path automatically.
[*]Create a file within [FONT=Courier New]~/bin[/FONT] called [FONT=Courier New]mogtime[/FONT] (you may choose a different name).
[*]Open [FONT=Courier New]mogtime[/FONT] (with [FONT=Courier New]gedit[/FONT] or your favourite text editor), paste in the code that I've pasted at the bottom of this post, and save it.
[*]Change the permissions of [FONT=Courier New]mogtime[/FONT] to allow execution (find [FONT=Courier New]mogtime[/FONT] in Nautilus; right-click and select Properties > Permissions > Execute > Allow executing file as program).
[/LIST]
**[SIZE=3]How to use[/SIZE]**

[LIST=1]
[*]Copy the files that you want to mogrify into an empty directory. This is important, because if my code has an error, you will still have your original files.
[*]Open [FONT=Courier New]mogtime[/FONT] and find the line within the code (line 51) that contains nothing but a backslash. Before the backslash, type all the parameters *exactly* as you want to pass to mogrify, but leave off the name of the file. For example, if you wanted to call mogrify with each file as:
[FONT=Courier New]mogrify -flip -implode 5 *filename*[/FONT]
then you would change the line so that that section of [FONT=Courier New]mogtime[/FONT] looked like this:
```
mogrify \
        -flip -implode 5 \
        "${FILENAME}"   # Change the line above this one.
```
[*]Save your changes.
[*]In a terminal, navigate to the directory with your copied files (not the original files).
[*]Enter the following command:
```
find -xdev -maxdepth 1 -name '*.jpg' -execdir mogtime {} \;
```If your files are [FONT=Courier New]*.png[/FONT], change [FONT=Courier New]*.jpg[/FONT] in the command to [FONT=Courier New]*.png[/FONT] (or whatever you need). This is the command that will run mogrify (via [FONT=Courier New]mogtime[/FONT]) on every file within that directory.
[/LIST]
Although I've tested the script, I have *not* done so thoroughly. Therefore, please be sure to run it in the copied directory and not on your original files!

*** And here is the code... (I hope it works well)***
```
#!/bin/bash

# Pass a file to mogrify, but retain the timestamp to the nearest second.
#
# Amend the mogrify line below with the correct parameters.
#
# Parameters:
#    The input file and nothing else.
#
# Return codes:
#    101    The file does not exist or is not a regular file
#    102    Did not have permission to read the file
#    103    Did not have permission to modify the file
#    Any other code: As returned by mogrify.

# Find the last parameter.
FILENAME="${1}"

# Check that the file exists and is readable and writeable.
if [[ ! -f ${FILENAME} ]]
then
    echo "The file does not exist or it is not a regular file:  ${FILENAME}" >&2
    exit 101
fi
if [[ ! -r ${FILENAME} ]]
then
    echo "I cannot read the file: ${FILENAME}" >&2
    exit 102
fi
if [[ ! -w ${FILENAME} ]]
then
    echo "I cannot modify the file: ${FILENAME}" >&2
    exit 103
fi

# Record the time stamp to the nearest second.
TIMESTAMP="$( ls -l --time-style='+%Y%m%d%H%M.%S' "${FILENAME}" | cut  --delimiter=' ' --fields=6 )"

# Mogrify the file.

#  ==================================================================================================
# Insert the parameters to mogrify on the line below 'mogrify'. Be sure  to end the line with a
# single backslash.
#  ==================================================================================================
mogrify    \
    \
    "${FILENAME}"    # Change the line above this one.
#  ==================================================================================================

RETURNCODE=${?}

# Reset the timestamp.
touch -t ${TIMESTAMP} "${FILENAME}"

# Exit with the appropriate code.
exit ${RETURNCODE}
```

---

### Post by BoneKracker on 2010-06-10
Nice work.  I'd say somebody owes somebody a pint. :p

---

### Post by Zill on 2010-06-11
> **Paddy Landau said:**
> I've knocked up something quick for you, Zill...
Many thanks for that Paddy - your script works perfectly and does *exactly* what I wanted. :-)

As BoneKracker suggests, I really owe you a pint.  However, I hope can make do with a bucket of popcorn for now. ;-)

:popcorn:

---

### Post by Paddy Landau on 2010-06-12
> **Zill said:**
> ... I really owe you a pint.
Pay it forward instead. One day you'll help someone else in an area where you are good.

---

### Post by Zill on 2010-06-12
> **Paddy Landau said:**
> Pay it forward instead...
Will do - and thanks again for all your work on this.  Much appreciated and I am sure your script will be of use to others in the future finding this thread via search engines. :-)

---

