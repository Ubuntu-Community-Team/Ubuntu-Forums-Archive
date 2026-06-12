---
title: "xdmcp"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by jonmartin on 2007-09-13
Trying to get xdmcp / kdm working on my kubuntu 7.04. I've edited /etc/kde3/kdmrc and /etc/kde3/Xaccess (uncommented the lines that are suggested in numerous postings about this)

But; It doesn't work. My kubuntu box shows up in the remote logon list on my other SuSE 10.2 machine. When I select to log on to it I get a black screen with the X-cursor on the SuSE box. On the kubuntu box "something" happens, from time to time, the screen goes black and I have to use Ctrl-Alt-F7 to get back to my local X session if I have one. 

Seems to be a lot of posts about this feature, but I've seen no solution yet ... what's up?

Why isn't there an entry in the system setup to enable this? On fedora (which is otherwise a mess) and SuSE (which freezes when enabling my nifty dual-core cpu) it's just a matter of ticking of xdmcp in the setup tools ...

---

### Post by kthxbai2u on 2007-11-06
I have a similar problem with 7.10. I click the menu at login and select remote login. When I enter the IP of the server on my network, and try to connect, I get the black background and X cursor also... Is that a problem with the server or the client? Is it some sort of configuration problem? You should be able to just turn it on and have it work properly shouldn't you? :P Anyways I'm out to continue looking for a solution to this. Keep you posted :D

~kthx :confused::confused: :confused:

---

### Post by kthxbai2u on 2007-11-11
I found a quick solution, but only works if you know how to load the app/w.e from console... I was just looking to use Quanta for PHP development, Here is how you can do this without XDMCP:

1) On the server, run "sudo apt-get install ssh" in console
2) On the client computer, Download Putty 
    - google putty if on windows
    - in linux, type "putty" in console. If not installed then "sudo apt-get install putty"

3) Load putty, by typing "putty &" in a terminal window. (or on winblowz open the .exe)

4) Before you connect, in the menu on the left side of the connect window, expand the "ssh" section and select "X11". Now click "Enable X11 Forwarding"

  - At this point on a Winblowz machine, you will have to browse to the url [url]http://cc.jlab.org/docs/services/windows/exceed/installExceed.html[url] and follow those steps O_o
     
  - At this point, If your on a Linux client, you will have done all the work. You already have  an X server to forward to :D.

5) Select "Session" from the menu on the left, and type in the server's ip or Host name in the space provided. 

   - Now is a good idea to save that profile

6) Hit connect. Login using your remote machines user accounts.

7) Run that graphical App as if you were on that machine. This is a secure shell connection :D For example, I would type "quanta &" (the '&' is to run it without locking up the shell - I can run more apps if i need)

Anyways I'm off to do some PHP. Hope this helps you untill they make it so you just turn on XDMCP and it works. It took a bit of probing, I just was playing with putty and noticed "Enable X11 Forwarding" and then googled it haha


[EDIT]This works perfectly! I use the "rpl" command to replace text in all my php files alot, so I already have a terminal open! Looove this workaround.[/EDIT]

[EDIT2]I can only open apps logged in as root for some reason. troubleshooting this. Post if you can log in to the server as a user other than root and start graphical applications.[/EDIT2]

kthxbai2u
admin@codinggroundz.com
http://www.codinggroundz.com/

---

