---
title: "Run a scrip when a file is saved"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by tij on 2010-05-24
"Hello world!"

Any suggestions on writing a script that will run every time a certain text file is saved, opened, etc?  

My intention is to output the lines in a specific vim file (~/foo) that have been added since the last time I saved the file. I have a vim file that is periodically edited by multiple people on a network and would like to run a script to tell me what has been added to this file since I last worked on it (this way I won't miss any additions to the file).  

I'm realizing as I type this that it may be more difficult than I imagine to distinguish between the last time "user 1" saved the file and the last time "user 2" saved the file... Any suggestions or thoughts about a more efficient way to accomplish this would be greatly appreciated.

---

### Post by SRST Technologies on 2010-05-24
Oh, man, you're probably going to need to set up a CVS server for that.

---

### Post by BoneKracker on 2010-05-24
I'm not sure what a "vim file" is (I will assume you mean a text file), but my approach to your requirement would be to save a backup of the file when I'm done editing.  Then, I could simply use 'diff' to do a comparison when I come back and want to see what has changed in the actual document. Hopefully, other users aren't editing files in your home directory, because then one of them might overwrite your backup, depending on their vimrc settings. You could get more fancy, but there's a point of diminishing returns, when the work to automate something far surpasses the time saved by doing so.

It might be useful to know more about this file (what's in it, what are you trying to do), because there might be a better way of handling this.

---

### Post by yaaarrrgg on 2010-05-25
As a quick and dirty solution, you can execute a shell script every time you want to edit the file.  Like:

#!/bin/bash
vi file
# then this will execute when you exit vi
/path/to/script
# or execute more bash comands
cp file /to/some/path/

Though of course if people use "vi file" directly, that totally goes around this approach.

---

### Post by SRST Technologies on 2010-05-25
A scripted method isn't going to help much in this case, fellas.  First off, you're going to need to provide the actual script to him.  This is a case of a person asking what kind of software is available to do this automatically, so the possibility that they can come up with this kind of shell scripting on their own is slim.

A CVS server sounds pretty perfect for his (her?) needs as a CVS server is going to keep past updates if set up right so they can revert backwards if needed and will keep records of who edited what when and how.

---

### Post by tij on 2010-05-27
Sorry about the delayed reply.

Thanks for the help. Indeed, my so-called "vim file" is a simple text file. All I wanted from my script (half for the functionality, half for the process of learning) was to see any changes that had been made to the file since I last edited it. I got it working with a combination of BoneKracker and yaaarrrgg's suggestions:


#!/bin/bash

diff /path/to/backup /path/to/shared/notes 
echo "would you like to edit this file?"
    read -e prompt
        if [ $prompt = yes ] #This gives me time to read the updates to the file before it loads in vim (sometimes thats all I need to do)
        then
            vim /path/to/shared/notes
            cp /path/to/shared/notes /path/to/backup
        else
            echo "exiting"
        fi

Pretty simple...but as my initial post said, I was looking for suggestions on "writing a script", not downloading software to do it for me.

---

