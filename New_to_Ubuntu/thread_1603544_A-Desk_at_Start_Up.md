---
title: "A-Desk at Start Up"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by ConfusedLinuxer on 2010-10-22
So I am completely new to Ubuntu, and I downloaded A-Desk on my laptop. The problem I'm having is I want A-Desk to automatically play Summer_Leaves.wmv at startup, but I don't know how to do it.
I have already right-clicked the desktop and sent the A-Desk Daemon to startup applications, but i have no idea what to type for the command. I've been fiddling with it for the past hour to no avail. I searched online and saw one other topic similar to mine, but nobody has responded in a while and I hope this topic sheds some light on my situation.
If any of you have any clue as to what I should be doing, I would greatly appreciate it. Thanks!

---

### Post by ArgusVision on 2010-10-22
Under System > Preferences you should see "Startup Applications". Click and add A-Desk. Log out, and back in, to test.

Edit: Perhaps I should read with a better focus on detail.... looks like you tried that.

When you say A-desk, do you mean A-desklets? Or another program? If it is another, where did you get it?

---

### Post by ConfusedLinuxer on 2010-10-22
Thanks for the quick reply! However, this is the part I'm stuck at. I already have A-Desk as one of my startup applications. It just doesn't do anything once I restart the laptop.
So far the following is filled in:
NAME: A-Desk Daemon
COMMAND: ~/./.autoinit
Assuming the video I want A-Desk to play at startup is located at "/home/bhumi/Downloads/A-Desk/Summer_Leaves.wmv" how would i modify the command?

---

### Post by ArgusVision on 2010-10-22
Is this the A-desk listed on gnome-look.org?

Ok. So the command you run from terminal is ~./autoinit ?

After you run this, does it prompt you for a file name?

Check the command in the start up. If you entered ~/./autoinit it's not going to work...

Sorry it took so long this time around.

---

### Post by ConfusedLinuxer on 2010-10-23
I have the free version (v0.17) and basically followed this tutorial:
[http://www.youtube.com/watch?v=WIbJ5S3PUJc](http://www.youtube.com/watch?v=WIbJ5S3PUJc)

I ran ~./autoinit in the terminal and it came back with a "no such file or directory" and when i put ~./autoinit in the command for the startup application, nothing happens when i turn on the laptop. I also tried "~/./home/bhumi/Downloads/A-Desk/Summer_Leaves.wmv/autoinit" for the command in the startup applications and when i log out and back in, still nothing happens. I can't even get the option to choose a video when i start up the laptop.

---

### Post by ArgusVision on 2010-10-24
Could you attatch the script since you have the free one, so I could take a look at it?
Maybe if I could see what it's trying to do I could give you a better answer.

---

### Post by ConfusedLinuxer on 2010-11-07
Sorry it took so long; some family matters came up and then i forgot my password and so on and so forth.

Anyway, here's what i found while perusing the script for a-desk:

"Auto-initiate") cp ~/.gnome2/nautilus-scripts/a-desk.desktop ~/.config/autostart/
    zenity --info \ 
    --text "Auto-Initiate A-Desk Activated !";;

If i still can't get it working, it's not really that big of a deal. Thanks for the help, though

---

### Post by dan1981football on 2011-06-14
Did you ever  manage to figure this out?

I can get up to the little box appearing asking you to select a video at startup but cant seem to work out how to get the movie from loading..

I'm pulling my hair out here :(

---

### Post by thundercat1989 on 2012-05-06
to get it to launch at startup open terminal  and type :
[LEFT]chmod u+x /home/USER/.autoinit
[/LEFT]



then go to prefrences------> startup applications---->Add----->browse to your home folder press ctrl+H (to show hidden files) then select ".autoinit" name it what ever you want. then bada bamm you got it working :guitar:

---

### Post by oldos2er on 2012-05-06
Old thread closed.

---

