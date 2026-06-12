---
title: "Desktop as  secure server"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Allus on 2008-02-20
Okay. I have Kubuntu Feist on my desktop, (dual boot with xp).  On my laptop I have Ubuntu Gutsy - sole install (harddrive crashed and M$ didn't give me any restore discs).

Now,  my main concern is using this laptop at wifi hotspots.  I want to know all my transmissions are secured.  I've tried to look into things like hamachi, but even though it's installed on both computers I can only ping the other machine. I cannot browse and I really don't see how this is securing anything.

Another poster mentioned using ssh and Socks in Firefox.  Well, this set me off into looking into SSH.  Now the way I understand it, (and I don't think I understand any of it), I need to set up my desktop as a server.  And then putty into it with the laptop. 

I've tried to go through a few tutorials on the web, but they seem only to deal with the client side of the setup, not setting up a home computer as a ssh-server. So, I:

/usr/sbin/sshd

and get my prompt back. 

Does anyone know of tutorial that will help me to set up the desktop as a ssh server?

---

### Post by Herman on 2008-02-20
> And then putty into it with the laptop. :confused: I thought 'Putty' was some Windows program to do with SSH? Don't know why you need that.

> Now, my main concern is using this laptop at wifi hotspots. I want to know all my transmissions are secured. I've tried to look into things like hamachi, but even though it's installed on both computers I can only ping the other machine. I cannot browse and I really don't see how this is securing anything. I don't know, I hope someone else can help you with the wireless security question.

>  Does anyone know of tutorial that will help me to set up the desktop as a ssh server?      :) I made one, it's still a work in progress, but it's an attempt to explain  firstly how to set up an SSH network beginning with the simplest possible setup, (a file rescue with a crossover cable), and progressing through a protected home LAN, and finally ending uo with port forwarding and how to connect to your home LAN from the  internet.
It's still a bit messy, but I'm working on it. 
Take a look, I hope you will find it some help. Here is the link, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm").

Regards, Herman :)

---

### Post by Allus on 2008-02-20
Thanks Herman.  Yes, that did help a little bit.  I got the server running on the desktop. And tried to loging through the command line on the laptop:

ssh -X UpStairsDesktop@172.23.76.1

This always gave me connection refused msgs, which made me think it was the server side that was problematic.  But, then I realized that my wireless setup did have DHCP and I looked up the IP it was assigned. When I tried that IP I got the correct messages and was prompted for a password. But it won't accept the password!

I tried the server's root password. Then the password of a user on the server. Then I tried my client user's password then i tried my router's setup page password.  I've tried every password I can think of.  The server will not accept any password.

So, that's my current problem.

My future question, (assuming I get beyond this basic), is:  Okay I have to use the DHCP assigned password while I'm on my network.  But let's say I go down to the coffeshop or off to another state to visit friends and relatives. Now I'm using their IP to connect. If I try to logon now, do I use the IP assigned by the router, or do I use the IP assigned by my ISP?

in re Putty:  I don't know.   Putty came with the installation or maybe I got it through the package manager.  One of the turorials I was looking at mentioned the use of Putty. So I was using that. 

Right now I'm using this tut to figure out to use X11:

[http://narnia.cs.ttu.edu/drupal/node/195](http://narnia.cs.ttu.edu/drupal/node/195)

But I'm still stuck at the password stage.

---

### Post by Allus on 2008-02-20
Okay.  The password issue:  I'm posting this just in case some other noob does the same thing.  My desktop is the server running Kubuntu. My laptop is the client. On the laptop I was trying to ssh in by addressing the root:

root@ipaddress  

But, on the desktop I was logged in as user!  This suddenly sunk in to my thick skull and I then ssh'ed in as user.  Now the password was accepted. Success!  Awwwww that feels good.

New problem. On the above mentioned tutorial I'm following the author says after login to type:

gnome-session

Well, the first thing that happened was I was notified that I didn't have gnome-session installed.  It told me how to install it if I wanted it.  So, I did that. As it was installing I noticed the text on the screen referring to feisty --  now, I have feisty fawn on the Desktop with Kubuntu. But my laptop uses Gutsy.  So, I guess the request was made to the Kubuntu machine through my laptop and the server was installing the software per the Kubuntu machine. 

Once it was installed I repeated the command. And I now got some errors about sound not being loaded.  I then got the graphic for the gnome-session, but it was totally unresponsive. I had to click the command window to exit.  I repeated the process with the same result. 

I went upstairs to my Desktop. in a command window I typed 'gnome-session' and was told that I already had a session running. So, I rebooted the computer and when I logged in, my KDE desktop was replaced by a brown screen with the nautilus graphic frozen in the middle of it.  I had to use Ctrl-alt-BKSP to get out and back onto a log-in screen. The same thing happened when I logged in as root.  

At the login screen their is an option to login in a variety of ways i choose the KDE option.  This solved that problem and I got my KDE desktop back again.

But what's the deal with the gnome-session.  This is complicated.  I don't know if the gnome-session on the laptop was damaged with the download.  And I don't know how I go about repairing the gnome on my desktop to get full functionality.

So, if anyone has any ideas about this I'd like to hear them. I will keep working at it on my own.

Thanks.

---

### Post by Herman on 2008-02-20
> My future question, (assuming I get beyond this basic), is: Okay I have to use the DHCP assigned password while I'm on my network. But let's say I go down to the coffeshop or off to another state to visit friends and relatives. Now I'm using their IP to connect. If I try to logon now, do I use the IP assigned by the router, or do I use the IP assigned by my ISP? I'm not experienced with wireless yet, but I imagine I would just try DHCP first, which will let your laptop accept whatever IP address the nearest wireless router wants to assign for the connection. 
The other way, static IP address, means your laptop will be insisting on a certain IP address, which might already be taken or might even be outside the range of the router.
> But what's the deal with the gnome-session. This is complicated. I don't know if the gnome-session on the laptop was damaged with the download. And I don't know how I go about repairing the gnome on my desktop to get full functionality. Probably that tutorial you were following was only written for Ubuntu and the author didnt anticipate that someone running Kubuntu would try to use it. I'm not sure of the Kubuntu equivalent of ' gnome-session', maybe if you had tried 'kde-session' it would have worked better?

Normally, we can install the gnome desktop in a Kubuntu system with a command like 'sudo aptitude install ubuntu-desktop' or something like that. 
Maybe you should try running that command in your Kubuntu computer, that might install a few more packages and get your gnome that you installed in it fully functional.
Or you could uninstall it with, 'sudo aptitude remove ubuntu-desktop' maybe. 
If it's not doing any harm you could just keep it, the only problem is you might have a few more updates to download now and again.
> This is complicated.  I don't know if the gnome-session on the laptop was damaged with the download.   I hope not, I wouldn't imagine it would be, are you noticing any problems? I think everything should be okay.

Thanks for the link to that tutorial you're using, by the way, I learned some new tips and tricks from it. :)

---

### Post by Allus on 2008-02-20
Hi again. No, I don't believe you can damage much of anything during these sessions unless you deliberately delete files from the remote computer.  

I've learned quite a bit since I started this thing last night. I wasted a lot of time trying to decipher errors from the gnome-session command.  The short answer is the one you mention: there is simply a different command to load the kde desktop.

I found the answer here:

[http://ubuntuforums.org/showthread.php?t=148614](http://ubuntuforums.org/showthread.php?t=148614)

Once logged onto the remote server just type "kicker&"   What this does is loads the kde task bar on top of the Ubuntu task bar on the client machine. You can navigate the entire system graphically that way. Amazing. I thought at least.

I could not get the remote machine to transfer sound.  I was surprised though. I typed in "Amarok" to see if I could get something to play. It seemed as though nothing happened except for some errors so I left it alone. Later I minimized the command window to find the Amarok program in the background. Again, no sound. But, I do not have Amarok installed on this machine, so the graphical interface was transferred to me.

I also have not figured out how to transfer a file over.  Supposedly scp will do that but I haven't yet got a handle on that command. 

One other thing I was mistaken about:  You don't need to be logged into the account on the server machine to access it through ssh.  When I first began I thought I was sshing into the root account when I was really using the machine name. There was no account name under that name. Being logged in as user, allowed me to ssh in as either user or root.  Now, I suppose that if you ssh in the root account you acquire full privileges of root. SSHing into the user account would limit what you could do.  I don't know, but it seems that's how it should be.

Anyway, been fun for the day. Except for file transfer I've been able to do everything I wanted.

---

