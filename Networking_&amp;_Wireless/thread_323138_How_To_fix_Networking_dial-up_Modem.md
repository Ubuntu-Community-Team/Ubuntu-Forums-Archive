---
title: "How To fix Networking dial-up Modem"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by FLPCGuy on 2006-12-21
If you can't get a modem connection to work in Ubuntu Networking it isn't you:

[http://www.markshuttleworth.com/arch...#comment-10942]("http://www.markshuttleworth.com/archives/63#comment-10942")
At the moment ubuntu/kubuntu is booby-trapped against dial-up users:
 **dial-up modem users must comment out the ‘auth’ line in /etc/ppp/options and create an empty /etc/resolv.conf file. **Once these two arcane measures are taken, dial-up modems work fine. This problem has been incorporated in every kubuntu since at least 5.04.

---

### Post by sdowney717 on 2006-12-21
Interesting
Most people cant figure out out linmodem winmodems anyway and use external hardware modems or ethernet.
If you want, switch to Fedora.
Just why are there so many linux distros out there?
What would make ubuntu better than fedora?

---

### Post by FLPCGuy on 2006-12-21
My post refers to the 'Networking' GUI in System Admin which is supposed to allow an ethernet or modem connection choice and configuration.  It is a very simple dialog but doesn't work by default for a modem connection, even with a full external modem like mine in recent distros of Ubuntu/Kubuntu (since 5.04?).                                                           
.                              .                          .                            .                    .                           After weeks of scouring forums a kind user gave me the answer above which now allows my selected modem network connection to work and fires it up on bootup.  I haven't yet figured out how to disconnect it other than to shutdown since there is no connect/disconnect feature (applet is obviously designed for always on broadband with the Modem choice added as an afterthought).  Internally, it is necessary to remove the auth line in /etc/ppp/options which blocks packets until you are authenticated.  That default config doesn't work with a dialup modem. 
                                                                                                                 To answer your question, one reason to use Ubuntu over Fedora is the Debian apt package manager which I think is better than RPM and can install almost any kind of package (over 22,000 apps in my choice of repositories) including DEBs and RPMs.
                                     I dropped RedHat when they abandoned the open desktop leaving me hanging and never went back when they started the Fedora project.  I'm sure it is still a fine distro, it always worked well for me.  If I added another distro to run besides Ubuntu/Kubuntu it would only be to try Suse 10.2.  I was very happy with SuSe 9.1 Personal, their last single CD release which is no longer supported.
                                                                                  Ubuntu isn't quite as easy as RedHat but I don't mind that it forces me to get under the hood and use terminal more often.  That's the only way to learn how your OS really works anyway.  Everything in XP can be run from a command line too, but I don't know anyone who can do it.

---

### Post by Jack the R on 2006-12-23
Man, thanks for posting that!  I just spent $21 on various cable adapters to get my old external modem to work with my new computer, just to discover Kubuntu can not find an external modem either.

Maybe this will work.

edit --

For those like me who are unfamiliar with code, look at the end of the sixth "paragraph."  See the only word without a # sign in front of it, "auth."  That's what you're looking for.  Put a # sign in front of it.

In regards to the original post, not ALL modems will work just because you make these two changes.  If you have a winmodem (the modem is a small card inside your machine), you still have to go through the linmodems.org process.  Your task has only begun.  If your winmodem is not supported, you have no choice but to go buy another modem (preferably external, these are all "real" modems, not winmodems which rely on your cpu and drivers to do the job).

---

### Post by FLPCGuy on 2006-12-25
> **Jack the R said:**
> Man, thanks ...  If your winmodem is not supported, you have no choice but to go buy another modem (preferably external, these are all "real" modems, not winmodems which rely on your cpu and drivers to do the job).


Sadly, many USB modems are controller-less now and require OS-specific software drivers.  Be sure you buy one that says it will work with Linux (and not just one particular kernel distro for which drivers are included). 

Linux REALLY NEEDS someone to write a software modem controller compatible with XP's.  Tens of thousands of potential users are prevented from using Linux for this reason alone.

---

### Post by MichaelSM on 2007-04-19
Thank you FLPCGUY. OK. for a start I couldn't log onto  shuttleworth but I don't know if that matters. I marked the AUTH with # as suggested. I just do what I'm told ... when it came to create an empty /etc/resolv.conf file. well, I went there and it wasn't empty. There were two entries: nameserver 198.142.0.51
nameserver 211.29.132.12
So what does that mean? Do I just delete them?  Step 1) didn't make any difference. so where to now? 
All help appreciated.
Thanks in anticipation, Michael.
PS I'm using or trying to use an external USR serial 56k modem. It works with everything else except Edgy.

---

### Post by FLPCGuy on 2007-04-21
> **MichaelSM said:**
> Thank you FLPCGUY. OK. for a start I couldn't log onto  shuttleworth but I don't know if that matters. I marked the AUTH with # as suggested. I just do what I'm told ... when it came to create an empty /etc/resolv.conf file. well, I went there and it wasn't empty. There were two entries: nameserver 198.142.0.51
nameserver 211.29.132.12
So what does that mean? Do I just delete them?  Step 1) didn't make any difference. so where to now? 
All help appreciated.
Thanks in anticipation, Michael.
PS I'm using or trying to use an external USR serial 56k modem. It works with everything else except Edgy.

The two nameserver entries just indicate where to get DNS info.  They shouldn't present a problem unless your ISP has made a change recently.  As I said, the Networking dialog in Edgy doesn't work well with external modems since it can't detect when they are connected.  I use KPPP to connect and ignore the Networking feature in Edgy.  I don't think they have fixed dial-up problems in Feisty but I haven't tried it yet.  Dial-up is NOT a priority at Canonical for some strange reason. (they dropped the dial-up bug priority to nothing).  Apparently, they are only interested in high-tech broadband users for now, especially wireless laptops which are a growing minority.

To get connected initially, from the terminal  run pppconfig which gives you a text dialog and menu.  Configure the default entry (provider) with your ISP info and ttyS0 for your serial port.  (I have no idea how to configure an external USB modem.  Check devices.). Once configured you can connect from the terminal with PON and disconnect with POFF.   You will have maximum bandwidth this way.  Some have reported a slower connection when using Networking.

Download KPPP from Synaptic pkg mgr for a graphical connection interface.  Because Networking will not detect your KPPP or PON connection, you won't be able to run certain network aware apps like Firestarter (iptables interface), etc.  but you will still be far safer by default than running any version of Windows!  With some fiddling you may then get Networking to use your modem (if a modem entry is present).  I couldn't get mine to store the configuration between sessions.  It will connect automatically upon startup and disconnect at shutdown.  Network awareness even connected this way is still problematic in Edgy.  Good Luck.

I've just ordered SuSe 10.2, Centos 5.0, and Kubuntu 7.04 and will report how well dialup and other features work with each of these distros in about three or four weeks.

---

### Post by jitsu on 2007-05-03
I've just become aware that I have a dial-up problem after trying to upgrade to Ubuntu 6.10.

I've just ordered a book to help me using the terminal.

I tried "etc/ppp/options" and couldn't get into anything.

If some kind individual might give me an idea of how to start I would appreciate it. Just to access the basic folder and I'll go from there.


thanks,
jitsu

---

### Post by FLPCGuy on 2007-05-04
> **jitsu said:**
> I've just become aware that I have a dial-up problem after trying to upgrade to Ubuntu 6.10.

I've just ordered a book to help me using the terminal.

I tried "etc/ppp/options" and couldn't get into anything.

If some kind individual might give me an idea of how to start I would appreciate it. Just to access the basic folder and I'll go from there.


thanks,
jitsu
To answer your specific question, click on Applications, Accessories, Terminal.  Type cd /etc/ppp/options.  That should put you into the correct folder.  You might want to make a backup copy of the original file first.  sudo cp options options.bkup  To edit the file I typed sudo gedit options.  You can undo any changes and replace the original file with 'sudo cp options.bkup options'.

There is an interesting discussion on Launchpad that may apply here:
                                       [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/22119](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/22119)
   
  
To summarize:
                                       [SIZE=2]According to syslog and settings in /etc/ppp/peers/* a device /dev/modem is assumed which does not exist. Instead, the real device name should be added (e.g. /dev/ttySL0 for smartlink-alsa-driver, /dev/slamr0 for non-free driver, /dev/ttyS0 for serial modem etc.) . Udev no-longer creates a /dev/modem link as far as I know. Only for "ttyLTM[0-9]*" (whatever kind of device that is, maybe lucent?) in /etc/udev/rules.d/60-symlinks.rules a symlink is set up. You may modify this setting according to your needs, too, if you want to have a /dev/modem symlink (which is still hardcoded for some programs).[/SIZE]
        [LEFT][SIZE=2]In Edgy this is caused by incorrectly setting the dial-out command to "ATDTW" or "ATDPW" instead of "ATDT" or "ATDP" in /etc/chatscripts/ppp0.[/SIZE][/LEFT]
        [LEFT][SIZE=2]The quick and dirty way to fix things for Edgy: Go to file /usr/share/system-tools-backends-2.0/scripts/Network/Ifaces.pm, line 3137 (subroutine get_interface_replace_table, section "debian-3.0") and remove 'W' from between %external_line% and %phone_number%.[/SIZE][/LEFT]
        [LEFT][SIZE=2][search for %external_line%W%phone_number% and replace with %external_line%%phone_number%][/SIZE][/LEFT]
    
   
  
Another solution goes like this:
                                       [http://www.ubuntuforums.org/showthread.php?t=6319](http://www.ubuntuforums.org/showthread.php?t=6319)
    
    [LEFT]If the setup of your modem failed using the Ubuntu metwork tools, you have at least two other options.[/LEFT]
    [LEFT] pppconfig[/LEFT]
    [LEFT] wvdial[/LEFT]
     
    [LEFT] pppconfig:[/LEFT]
     
    [LEFT] Open a terminal and run
 [/LEFT]
    [LEFT] sudo pppconfig[/LEFT]
    [LEFT] Enter the information as needed. Use the name 'provider' for your default connection. COM1 is /dev/ttyS0, COM2 is /dev/ttyS1, and so forth.

[/LEFT]
    [LEFT] Add your user to the dip group using the advanced options.[/LEFT]
    [LEFT] Save and exit.  To dial-out from the terminal run:
[/LEFT]
    [LEFT] sudo pon[/LEFT]
    [LEFT] If you get nothing or if you run into trouble, open another terminal and do:[/LEFT]
    [LEFT] sudo tail -f /var/log/messages[/LEFT]
     
    [LEFT] This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.[/LEFT]
    [LEFT] sudo poff hangs up.[/LEFT]
   
Once connected to your ISP, you can run System, Synaptic Pkg Mgr and download a GUI dial-up app like KPPP which is easy to configure and use.

Hopefully, one or the other of these solutions will get your external modem working again.

---

### Post by jitsu on 2007-05-04
FLPCGuy:

I appreciate your help.


thanks, jitsu

---

