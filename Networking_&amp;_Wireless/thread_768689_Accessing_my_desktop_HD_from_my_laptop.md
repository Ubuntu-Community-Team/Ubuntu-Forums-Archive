---
title: "Accessing my desktop HD from my laptop?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by 0liv on 2008-04-26
Hi there,

I'm trying to setup my home network. I've already read through the Ubuntu website but can't find what I need (or don't understand what I've read?).

So I need your help.

I own two computers (1 desktop & 1 laptop) and a WiFi modem-router. I'm using Ubuntu.

I'd like to accesss (wrx) the desktop partitions from my laptop when the former is running.

So what do I need to do? Could you please be as verbose as possible as I'm no Linux-geek yet (and totally new to LAN).

Many thanks in advance for your help!

--0liv

---

### Post by 0liv on 2008-04-28
Nobody?

---

### Post by whitefort on 2008-04-28
Well...  I'm pretty much a beginner too, but until someone can give you a better answer, here's my setup.

I have an Ubuntu PC, an Xubuntu PC, and a Ubuntu laptop.

In 'network settings' I give each of them a static address - you know, like
192.168.0.4

Then in synaptic I make sure that openssh-server is installed (openssh-client is installed by default).

And that's essentially it.  I can open a terminal (say on machine 192.168.0.4) and access machine 192.168.0.6 by typing 'ssh 192.168.0.6' and entering that machine's password.

Or, for nautilus, I can use the menu 'PLACES/CONNECT TO SERVER and fill in the details - SSH as the 'service type', the static address as the 'server', my username, and even the folder I want to open (for me, /home/john/)

I'm not at all sure that this is the best or 'real' way to set up a Linux network, but it works just fine for me.

Oh, and if you decide to try it, it can get tedious having to keep typing stuff like '192.168.0.6'  Instead, you can edit the etc/hosts file on each machine to link the static address to the machine's name.

This means, for example, instead of having to type 'ssh 192.168.0.6', I can just type 'ssh Athens' or 'ssh Sparta' depending on the machine.

I'm not sure I've explained this very well... if you think you want to go this route, feel free to ask any questions.

I like this setup because it gives me complete control of every machine from any other - for example, if I'm in the bedroom using my laptop and remember that I forgot to turn off the machine downstairs (which is called Sparta), I can just open a terminal on the laptop, type 'ssh Sparta', and then 'type sudo shutdown -h now' and it will power down Sparta without me even getting out of bed, hehehe!

---

### Post by 0liv on 2008-04-28
Thanks... this seems very interesting !

Could you help me a bit more?

> In 'network settings' I give each of them a static address - you know, like 192.168.0.4


Where can I configure those "network settings"?
How do I give my computers such static adresses?
Do I need to do this on each computer or I can do it from only one?

> Then in synaptic I make sure that openssh-server is installed (openssh-client is installed by default).


Okay, done!

> Instead, you can edit the etc/hosts file on each machine to link the static address to the machine's name.


What lines do I have to put in the /etc/hosts/ ?
On which computer(s)?

Thanks in advance!

---

### Post by whitefort on 2008-04-28
Um...  Ok, now I'm getting scared!

Like I say, I'm pretty much a beginner myself, and I'm afraid of telling you something that messes up your wireless setup.

But here's what I did...  If you try to follow these steps, it's all at your own risk, etc, etc,  OK?  I'm still hoping someone more qualified will jump into this discussion...

1.  make sure openssh-server and openssh-client is on each machine.
2.  Menu item System/administration/Network to open the network settings.
    (this is where it got scary for me, as I lost my wireless connection a few times until I figured it out).

    Find your connection and click the 'properties' button.  you'll probably find 'enable roaming mode' is on by default.  I turned this off.
    Then in 'configuration', I selected 'static IP address'.

    Underneath that, I filled in (on this machine) 192.168.0.3
    (again, my lack of knowledge is showing here. I THINK the first 3 numbers need to be 192.168.0. and you can pick anything as the last one. I may be totally wrong!)

    Underneath that, the 'subnet mask' should automatically fill itself in as 255.255.255.0

    And underneath that (and I'm REALLY clueless here) I just tried 192.168.0.1, and it worked OK.  I'm guessing this maybe refers to my router or something...

   Click OK.

I seem to remember that I had to re-enter my wireless details, wireless password etc - I think that was where I had the panicky 5 minutes before I got things working again.

Anyway, if you get this far on each machine (giving them each a different static IP address, of course) and find that you still have wireless, can still connect to the net, etc, the rest is easy.

From one machine open a terminal and type 
ssh (followed by the static address of the other machine)
Since it's the first connection, a warning/question will pop up.  Just say 'yes'.
Then it will ask for the password of the other machine, and when you enter it, you'll be into that machine.  As a quick test, you could type 'eject' and the CD tray on the target machine should pop open.

I'm not so hot with terminal stuff, so I usually use the 'connect to server' option to access the target computer via nautilus.



Oh, and about 'etc/hosts...

I think you need to be root to change it.
Enter gksudo nautilus
This will open nautius with root powers, so be careful!

open ect/hosts...  I forget what a 'virgin' copy looks like, but here's mine after I changed it:  This is for machine 'Athens' -  Poser, Sparta and shark are my other machines, with the addresses I picked for them.

Remember to backup etc/hosts before messing with it (I didn't, but I was lucky, and it all worked)


==================================================

127.0.0.1	localhost
127.0.1.1	Athens

192.168.0.2  Poser
192.168.0.5  Sparta
192.168.0.7  snark



# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
================================================
    
Now that I have this hosts file in machine 'Athens', it knows that, for example, 192.168.0.7 is 'snark', so when I use ssh or 'connect to host', I can just type snark instead of 192.168.0.7

I hope this all gives you some pointers in the right direction, but I'd be a lot more comfortable if you hunted out a bit more info before trying it, especially in the area of changing your wireless network settings.

I'd hate to lead you into a minefield!

---

### Post by 0liv on 2008-04-28
Thanks! and don't fear! Even if I have a problem, I'm sure I can find out how to restore my connection!

BTW, I found that when I right-click the network connection icon in the top bar (showing two widescreens), I can have some Connection Informations. These gave me the current address of my computer: 192.168.1.100.

So I tried "ssh 192.168.1.100" in a terminal of my other computer... And nothing happened. I even don't have the prompt back, just like if the command is waiting for more option to go. I had ctrl-Z.

Anybody can give us more detailed explainations?

---

### Post by whitefort on 2008-04-28
> **0liv said:**
> the current address of my computer: 192.168.1.100.

So I tried "ssh 192.168.1.100" in a terminal of my other computer... And nothing happened. 

Um...  not sure about this.  You definitely have the open-ssh server on the computer you're trying to connect to?

One other thought - something similar to this happened to me when I installed firestarter (the firewall controller) on a target machine. Do you have anything like that running?  By checking my firestarter panel, I was able to see that the connection was blocked, and to set up a 'rule' to allow it.

---

### Post by 0liv on 2008-04-28
Oops, I forgot FireStarter. This was the problem.

Thanks a lot Whitefort!

I'll experiment a bit with ssh then post again.

---

### Post by 0liv on 2008-04-29
Hi Whitefort,

Fudging with my system, I discovered NFS. 
It's more intuitive to use than ssh.
And it's far more easy to navigate through the host shared folders as you can mount them directly it your directory tree.
If you need some info about it, just ask.

---

