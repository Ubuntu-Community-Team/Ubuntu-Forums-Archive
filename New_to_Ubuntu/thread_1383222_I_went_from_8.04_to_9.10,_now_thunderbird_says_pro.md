---
title: "I went from 8.04 to 9.10, now thunderbird says profile in use with my copied profile"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by laymon on 2010-01-17
I recently backup up my home folder on a different old drive I had (which had some kind of RAID flag that took me 2 hours to figure out how to mount it - but that is a different problem) before updating from Hardy Heron to Karmic Koala.

I followed the steps as follows:

[LIST=1]
[*]Locate your Default Thunderbird Profile folder named "XXXXXX.default" where the X's are a random mix of numbers and letters.
[*]                                 Copy the files in "XXXXXX.default" directly to the "new" computer over the network, or you can use a removable storage device such as a USB thumb drive or CD-R. Don't copy over the directory named "XXXXXXX.default", but just copy the files in the directory.
[*]                                                                                                   Download, install and run Thunderbird on the "new" computer. A new Default Profile is created when you run Thunderbird for the first time.
[*]                                                                                                   Shut down Thunderbird.
[*]                                                                                                   Move the files you copied from the Default folder of the "old" computer to the Default Thunderbird Profile folder ("XXXXXX.default") on the new computer. Again, you're moving the actual files in the old "XXXXXX.default" folder.
[*]                                                                                                   Launch Thunderbird on the "new" computer. Your old settings and emails should be available on this new installation.
[/LIST]

When I follow this it loads once, and then after I close, when I start thunderbird, I get:
"Thunderbird is already running, but is not responding. To open a new window,you must first close the Thunderbird process, or restart your system."

So then after searching about this, I followed :
[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)
including reading and using the man killall for correct (I think) usage.

So then yet more searching to find out how to use ~$ sudo thunderbird -profilemanager to create a new profile pointing to a copy of the folder (but ensuring no .lock or .parentlock files in folder). Variants of this process include but haven't been limited to (after a completed uninstall, reinstall cycle using synaptic package manager for each variant):

[LIST]
[*]store profile folder in different folder than .mozilla-thunderbird (and point to it using the profile manager, and then once with just manually editing the profiles.ini file
[*]copy all info from old folder into new default, and new created profile folders
[*]copy selected info from old folder into new default, and new created folder
[*]pointing toward the folder in its original location on the separate drive
[*]using a completely different profile set from a different backup on external from 2 weeks ago.
[/LIST]
Any ideas?

I am pretty sure it shouldn't be this hard. Please let me know what obvious thing I must be screwing up.

---

### Post by laymon on 2010-01-17
Update: I have chanced upon the interesting fact that I can run it with Terminal using "sudo thunderbird" ...

It starts dependably that way. loads all old mail and gets new mail from the servers. this is using my final attempt which was to copy all info into the folder after a clean default profile made by reinstalling after deleting all info from the folder, then copying the files into the new folder after runonce.

I checked permissions on the folder and they are set to my username for read/write and access...

---

### Post by cariboo on 2010-01-17
The easiest way is to edit profiles.ini to point to your default directory. profiles.ini is located in ~/.mozilla-thunderbird. It is a hidden directory. To access it in nautilus, open Nautilus ( places-->home folder), and press Ctrl-h, this reveal the hidden files and directories, then just right click the file and select open. It will open in gedit.

---

### Post by laymon on 2010-01-17
> **cariboo907 said:**
> The easiest way is to edit profiles.ini to point to your default directory. profiles.ini is located in ~/.mozilla-thunderbird. It is a hidden directory. To access it in nautilus, open Nautilus ( places-->home folder), and press Ctrl-h, this reveal the hidden files and directories, then just right click the file and select open. It will open in gedit.


Thanks for the reply,** cariboo**... that is one of the things I listed in the first bullet point, second section of my first post. I have tried editing that file to point at new folders, old folders copied into new locations, even to non relative locations on the backup drive. I understand how to edit the file, thanks to the documentation provided by Mozilla. I can find these files easily (control+h under nautilus running as gksudo, since the Ubuntu flavor seems to want to save me from myself ;)). 

The problem is that that I have tried everything I can find in this forum and in Mozilla's forums and documentation.

None of that seems to get me back to my previous ability to simply click an icon and start Thunderbird with all of my emails there and with all of the folders autodownloading new messages. I can't lie, I hate spending a lot of time in command line... 

As per my above post about running thnderbird as sudo, I have edited the app launcher in my panel to run "gnome-terminal -x sudo thunderbird" and it seems to launch properly, but I don't like to have a terminal open for launching thunderbird, nor do I like the idea that I have to run thunderbird as sudo. It shouldn't need that.

---

### Post by laymon on 2010-01-19
No other help? :(

---

### Post by laymon on 2010-01-19
I also can mention that I am unable to follow hyperlinks in emails. It gives the profile in use error, but for Firefox?

---

### Post by nanotube on 2010-01-20
probably a file ownership problem...
see the solution in this thread (using 'sudo chown -R'):
[http://ubuntuforums.org/showthread.php?t=1385563](http://ubuntuforums.org/showthread.php?t=1385563)

---

### Post by laymon on 2010-01-20
> **nanotube said:**
> probably a file ownership problem...
see the solution in this thread (using 'sudo chown -R'):
[http://ubuntuforums.org/showthread.php?t=1385563](http://ubuntuforums.org/showthread.php?t=1385563)


:D:D:D:D:D:D:D
Thanks nanotube. I had checked ownership on the subfolders but not the .mozilla-thunderbird. Marking this one [Solved]

---

### Post by nanotube on 2010-01-20
> **laymon said:**
> :D:D:D:D:D:D:D
Thanks nanotube. I had checked ownership on the subfolders but not the .mozilla-thunderbird. Marking this one [Solved]

great! :)

---

