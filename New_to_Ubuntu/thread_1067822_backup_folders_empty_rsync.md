---
title: "backup folders empty rsync"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Kellemora on 2009-02-12
Hi Gang

Hunted through all my notes but couldn't figure out what we did to solve this problem.

Rsync is copying all the folders, shows it's copying the files too, but viewing the backup shows all the folders there, but they are all empty.

using:
rsync -r -n -t -p -o -g -v --modify-window=1 /source/ /destination/

which is an exact duplicate of the command I have been using all along!

And yes it gives a million red error lines saying couldn't CHANGE permissions, etc. ad infinitum, but it's always done that!

Except its NOW adding the words FAILED and OPERATION NOT SUPPORTED.

Copying a File from one drive to another is NOT SUPPORTED in rsync?

The ONLY CHANGE I've made here, was I switched to my new computer, finally.  It's still 64 bit, but it looks like since now rsync is not supported in the 64 bit version, perhaps I should go back to the 32 bit version.

FWIW:  I DON'T want rsync CHANGING anything, just COPY files from one drive to another.  It continually tries changing ownership, permissions and then giving an error when it can't.  But at least it USED TO copy the file to the backup drive anyhow.

What's crazy is I can go to a Windoze machine and backup my Linux file server from one Linux box to another Linux box with no problems.
But trying to use Linux with Linux has ALWAYS been a problem, one error after another.  And now just empty folders.

Anything else to try besides Unison since rsync messes up so much?
Or should I use the old reliable Windows programs again?

TTUL
Gary

---

### Post by DGortze380 on 2009-02-12
No time to go through and figure out all your flags right now.

To copy one directory to another using rsync:

(sudo) rsync -ax /Path/To/Source /Path/To/Destination

-a  : archive mode
-x  : one file system (you'll probably want this, read the man pages)

to sync the destination with the source instead, add the --delete flag.

man rsync for more information.

---

### Post by Metallion on 2009-02-12
I usually use rsync -truv /path/to/source /path/to/destination and it always works for me. Does exactly what you ask: copy the stuff and no more. It sometimes gives me the error of setting permissions too but it never breaks the copying.

---

### Post by Kellemora on 2009-02-12
Hi Guys

First, the -n is NOT in my working file!
To save typing I hit a Dry Run to get the codes I was using to copy them.

OK - I tried BOTH of your methods!

It appears I can't use the -a due to symlinks I can't transfer to the file server and the -a also included -D which requires Super User or ROOT.

My rsync command is actually very simple:
-r is Recursive
-t is Preserve Time
-o is Preserve Owner
-p is Preserve Permissions
-g is Preserve Group
-v is Verbose

I do you --delete on occasion, but NOT backing up the daily file server just in case somebody deleted something out of orneriness.

I completely Deleted EVERYTHING in the particular folder I'm trying to write to, to make sure that no files are being copied over.

Rsync IS creating ALL of the folders from the Source Drive onto the Destination Drive, but not a single file is being copied over.  Every single one is giving FAILED, Operation Not Permitted (59).
I also get some permission problems as usual.

Out of curiosity, I ran rsync on the original computer this one replaced and it worked just fine.  It copied all of the files I purposely changed over to the File Server, just like always.  I also checked permissions of the Source File and compared it with the permissions on the Source File on this new computer.  They are identical!

It seems like I tried using that -x when I first started using rsync and it caused a problem with an ability to write to the file server.  The file servers main drive is NTFS and the drives in the computers are EXT3.
Seems like by removing the -x is what made it start working.

I wonder if I'm missing something on this new computer the other one has for NTFS?  But it shouldn't matter though.

In trying to refresh my memory on some of this (easy to forget when things are working as they should).  Early on we did everything as a FETCH rather than a PUT, meaning we never tried to put something from one computer ONTO another, we would only DRAW the info from the computer to the one we wanted it on, this was the only way to preserve permissions.
But this ceased to be a problem after we built the data file server.

However, in trying to get this 64 bit machine set up, I've run across numerous other problems since posting this.
I think my best bet is to Delete the 64 bit completely and return to 32 bit.  
No Adobe for 64 bit, No PDF Plug-in for 64 bit, even using the 32 bit Firefox, No Java for 64 bit that works with a plug-in, and I tried Iced Tea, didn't make any difference.  And a couple of programs I must run in WINE won't work on the 64 bit version either.

Good thing I have 8 computers here!
Trouble is, only this new one is 64 bit and the major problem child now!

Thanks for trying anyhow guys!

TTUL
Gary

---

### Post by Kellemora on 2009-02-12
Hi Guys

Well, I finally got it to work by working in REVERSE like we did way back when I first started using Ubuntu!

Went back to using Fetch instead of Put for the operation and it worked with ZERO errors!  And no files at all missing!

TTUL
Gary

---

