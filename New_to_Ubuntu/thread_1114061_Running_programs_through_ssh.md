---
title: "Running programs through ssh"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by championboxes on 2009-04-02
I currently have a older computer running xubuntu in the other room... Its not hooked up to a monitor/keyboard/etc... so I have been using vnc & ftp to use that computer through my local network...

Lately I have been fooling around with ssh and found out I can run my programs through ssh which is way more efficient due to vnc and the "ancientness" of this computer...

but basically I have a few questions about ssh 
1. should I worry about security?  as in running programs like transmission or firefox
2. is there a way to make xubuntu startup and login automatically but not the graphical part and still be able to connect and run those programs through ssh?
3. not a ssh question but a bash question is there a way to show all programs that are installed on the machine and what to type to run them?

---

### Post by durand on 2009-04-02
SSH stands for secure shell so it will encrypt everything between the two computers. So you don't have to worry about security. Just make sure you have a good password for each user and you'll be fine.

I'm not exactly sure what display manager xubuntu uses but you can disable it using:
```
sudo update-rc.d gdm remove
``` where gdm is the xubuntu display manager. 
It will then not start at all when you turn on your computer however non graphical programs will still work properly when you log in to ssh.

If you want to run graphical programs, you need to start ssh with the -X flag. It will then pipe all the xserver stuff to your current xserver and everything will be drawn on your computer. Just beware that it will continue to use the old computer's gtk theme and fonts and stuff like that.

To show what programs are installed, you could start synaptic in ssh -X or in the shell, you can press tab and it will display all the programs in an ugly list. bash supports tab completion so you can just type in the first few letters of a command and press tab and it will complete it.

---

### Post by championboxes on 2009-04-02
Ok cool so the only other questions I have is if i disable xfce the display manager whenever I turn the computer on will it still automatically login? or would it matter with using ssh?
> you could start synaptic in ssh -X or in the shell lol idk why I didnt think of that! thanks for your help

also one other thing do you think there would be a performance increase if I kept xfce from starting?

---

### Post by durand on 2009-04-02
With ssh, you will have to login anyway. You could get ssh to automatically authenticate it with magic cookies, I think. I haven't used that in a while but it will automatically log you into ssh if you are connecting from a certain machine.

It depends on how old the machine is. It might be that you won't have much ram left over if you keep xfce running. I try not to be wasteful so I usually just run the programs that I need. It would probably improve your system performance but maybe not by that much...

I have an old computer which I just use for bittorrent and as a media server and I keep boinc running on it all the time when it's turned on. I only ever notice a slowdown when I'm running some intensive graphics program like deluge torrent with about 50 torrents running. So, you normally shouldn't have a problem...

---

### Post by bodhi.zazen on 2009-04-02
If you disable GDM, then no, you will not automatically log in.

I suggest you look at ssh security :

[AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH") 

I tunnel VNC over ssh :

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

The other application you will want to look at is screen.

Screen allows you to run a command line session , and detach and log off your ssh session, but application on the sever continue to run.

[http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen/](http://www.rackaid.com/resources/linux-tutorials/general-tutorials/using-screen/)
[http://magazine.redhat.com/2007/09/27/a-guide-to-gnu-screen/](http://magazine.redhat.com/2007/09/27/a-guide-to-gnu-screen/)

So long as you have secured your server, ssh is rock solid in terms of security and forwarding X apps.

You can also forward X sessions with Xypher

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Or multiple X sessions

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

The last links would need to be adapted, but you get the general idea from the first link.

---

### Post by aeiah on 2009-04-02
you mentioned transmission, but deluge would be a better choice. you can set it to run as a daemon, and then connect to the daemon over the network with your normal computer. it'll behave more or less like it would if it was running locally, except when you turn your pc off it'll carry on downloading, since the backend is on your xubuntu box.

---

