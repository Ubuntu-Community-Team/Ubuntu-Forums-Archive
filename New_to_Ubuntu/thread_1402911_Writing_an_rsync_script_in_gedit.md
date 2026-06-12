---
title: "Writing an rsync script in gedit"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Matthew M on 2010-02-09
Hey, 
I'm trying to write a script in gedit that I can run using a desktop shortcut.
The script should back up 6 specific folders from my home directory to my external hard drive. I don't know what I'm doing here, so I figured I'd ask you guys before I go ahead and run anything...

WHAT I HAVE SO FAR:

```
#!/bin/bash
clear
rsync -avn --progress /home/matthew/Videos /media/FreeAgentDrive/backup/matthew/Videos && 
rsync -avn --progress /home/matthew/Music /media/FreeAgentDrive/backup/matthew/Music && 
rsync -avn --progress /home/matthew/Documents /media/FreeAgentDrive/backup/matthew/Documents && 
rsync -avn --progress /home/matthew/Software /media/FreeAgentDrive/backup/matthew/Software && 
rsync -avn --progress /home/matthew/Pictures /media/FreeAgentDrive/backup/matthew/Pictures && 
rsync -avn --progress /home/matthew/Downloads /media/FreeAgentDrive/backup/matthew/Downloads
echo
echo All done! You may disconnect your external drive now.
```lol so it's nothing too fancy. I have the -n command in my rsync lines so that I could run it in terminal and just do a "dry run" instead of actually doing things. It seemed to do what I expected it to then, but I really don't know. Is the #!/bin/bash at the top necessary?

And, once I decide I do have a satisfactory script, where would I go about saving it so that I can execute it using a simple desktop command? (or what would that desktop command look like?)

Thanks!

Matthew.

---

### Post by Orion8 on 2010-02-10
Hi, Matthew.

I am not a huge script master but I think you want to put the argument after your echo command on quotes, like 

```
echo "All done! You may disconnect your external drive now."
```

I have never tried to daisy-chain rync commands like you do -- I don't see why it would not work.  I just do my entire user home, excluding any *.iso files as they are huge and *.mkv files as I do them separately.  

My script looks like this:
```
#!/bin/bash
# This script mirrors orion's home folder to a folder on david.  iso images are ommited.  Check out rsync man for switch options.
rsync -avzh --progress --delete --exclude=".*/" --exclude="*.iso" --exclude="*.mkv" /home/orion/ /media/david/backup/orion_ubuntu_9-10
echo "rsync procedure complete"
```

I run it daily and it works great.

As for executing your script, I'd save it in ~/bin (that is, /home/matthew/bin).  If you don't have such a directory make it.  This director is automatically in the paths that your computer searches for executables.  If you are interested in seeing what the others are open a terminal and type ```
 echo $PATH 
```  The results are where your system looks for executables.  It requires root privileges to write to most of these places, and the executable is accessible system wide to other users so I'd recommend keeping it local and thus use ~/bin.

So, copy your file to /home/matthew/bin.  Open a terminal and type ```
cd bin
``` and then ```
chmod u+x scriptfilename
```  Another way to do this is to open Nautilus, navigate to ~/bin, select the script file, right click, and check the "make executable" option.

To execute you can hit alt-F2 and then type in the script filename and enter, or open a terminal and enter the script name.  Or... if you need more options, you could right-click your menu bar and add a launcher, using your script filename as the command and picking whatever icon you like.

I hope this helps.

---

