---
title: "ubuntu 10.04 starts in tty1 console; GUI does not load/start"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by udayspatel on 2010-08-05
Hello,

I've come across a very very strange issue with my ubuntu today. When I start my machine it only starts in TTY1 console and does not load/start GUI

I have tried the following but nothing seems to have worked.
[COLOR="Blue"][I][B]1) Used Alt + Ctrl + 7 : It only shows a blank (black) screen with no change for long time.
2) startx : Started in recovery mode to go to root prompt and then entered startx but it aborts the command
3) sudo service gdm start: It shows the pid of the service but does not start the gui.[/B][/I][/COLOR]

I am running from one problem in to another with Linux. Frankly it has been a bit overwhelming as I spend more time fixing the system then actually working on it. Is this a common experience or is it just my machine? The only thing that keeps me going and keeps me hooked to linux is the forum support. Everyone on the forum is so helpful. I love the open source community and want to be here forever reaping benefits and helping others!

Any help on the above topic is well appreciated.

Yudi

---

### Post by udayspatel on 2010-08-05
Update!
[COLOR="Blue"]When I run the _*startx*_ command, I get[/COLOR]
[SIZE="2"][COLOR="red"]X: /tmp/.X11-unix has suspicious mode (not 1777) or is not a directory, aborting, giving up
xinit: No such file or directory (error 2): Unable to connect to X server
xinit: No such process (error 3): server error[/COLOR][/SIZE]

[COLOR="blue"]By giving command: _*sudo service gdm start*_, I get[/COLOR]
[COLOR="Red"]gdm start/running, process 1047[/COLOR]

---

### Post by arinr73 on 2010-11-04
I have the same problem, I upgraded to maverick from lucid, i am having acer 4530 laptop with nvidia geforce 9100M g graphics card. sudo dpkg-reconfigure xserver-xorg results in this: /usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.

---

### Post by dajasc on 2011-01-16
Why is this marked solved?  There is no solution given and no link to a solution.

---

### Post by phatcartoon on 2011-02-24
I'm not 100% why this is considered [SOLVED], but I'm going to post what solved the problem for me. . . I had a problem finding a solution anywhere for this, and it might not be the best solution, but it worked for me. . . If you know a better solution, please correct me and post one.  


I believe this happened to me after an update on my video card, but I could be wrong. . . 

Once at the screen with the "TTY1" and login in. . I logged in.
Now, I'm logged in and at what looks like a terminal interface(no window or GUI) I changed the directory to. . .

cd /etc/X11

And, I renamed the, 'xorg.conf' file to something of non-importance. . 'xxxorg.conf' . . . or what ever you want.

mv xorg.conf xxxorg.conf


I then restarted my computer and I was able to log into the regular GUI interface.   My display settings were of course a bit messed up, but I was able to access the GUI at this time.  

I ran all my updates though the update manager and restarted my computer.  
After the restart I used Nautilus to navigate back to that xorg.conf file that I renamed and changed it's name back to, 
'xorg.conf'

Restarted my computer one last time and everything worked perfectly afterwards. . .  

If you have problems with low graphic settings make sure you card is active in the [Additional Drivers] and that your, [Visual Effects] is switch back to 'Normal' or 'Extra'


I hope this helps. . . And, like I said, this might not be the best way. . I was a bit stoned at the time,  . .but this method worked for me.

---

