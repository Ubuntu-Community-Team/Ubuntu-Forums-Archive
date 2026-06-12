---
title: "PC used primarily as file server - can Ubuntu ...?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Steven_S on 2009-05-06
Hello all! My first jump into Ubuntu (shakes). 

After searching high and low, I have bought a second-hand pc to use primarily as a file server. 

I say "primarily", because I also want it to be able to do other things: 

- use a browser
- run some simple photo editing/sorting software (such as Picasa)
- run a video player (I love VLC)
- run DVD and CD ripping/conversion/archiving software
- be able to burn the occasional CD or DVD
- run a music player and perhaps mp3 library software
- I need to be able to upload things using that system (Flickr Uploadr mainly, just give it the commands and let it run)

And stream to other pc's, but I guess that is not problematic. 

Also, I do not want RAID. I will simply mirror an internal drive to another internal drive (and use backup with a 3rd usb drive). The OS will sit on a separate IDE HDD.

So, you see, it is not really a dedicated file server. 

Windows XP comes pre-installed, but I would really like to try another OS while I'm at it (even if in dual boot). 

So, two questions that are probably easy to answer for someone who runs them, but I haven't found the answer yet:

- Can the Ubuntu server OS also be used to run the software I described?  

- Can the Ubuntu desktop versions do the (probably simple) server tasks of backing up connected systems, mirroring, making files available through from the outside world via a web interface or ftp,... ?

And, of course, will I be able to do it all through a GUI, or will I have to get my hands dirty? :)

The alternative is to use XP, but I am a bit worried that it won't be safe to run once the updates disappear. Plus, then I will need stuff like antivirus, firewall, ... and will need to figure out how to format in ext2 or ext3. That last one is because I want to make sure I can read the drives from any system, should the other hardware fail (which is also why I don't want to use RAID).

Oh yes, I would run it headless (from my laptop). 

Any thoughts and experiences? Other recommended OS's?

Many thanks for your insights!

---

### Post by Vunutus on 2009-05-06
I'm not an expert in this sort of thing but I everything you just posted can be accomplished fine from a standard desktop edition of Ubuntu, which is what you will want if you desire a GUI. As I understand it, the main thing that makes the server version of Ubuntu different is that it comes without a lot of the "fluff" found in desktop releases (the GUI, media programs, browsers, etc). 

The beauty of Linux is that virtually any distribution of Linux can become anything. You aren't restricted to certain tasks just because you installed a "home" version.

---

### Post by Steven_S on 2009-05-06
Thanks for that! I might give Linux Mint a spin. As it seems to be more or less the same as Ubuntu, I should be able to use all the help in here. 

I will have one HDD for the OS, and 2 or 3 1TB disks for storage. Do you think it will be easy to partition these disks in ext3 and to share them with a Windows system over the network?

---

### Post by perlluver on 2009-05-06
> **Steven_S said:**
> Thanks for that! I might give Linux Mint a spin. As it seems to be more or less the same as Ubuntu, I should be able to use all the help in here. 

I will have one HDD for the OS, and 2 or 3 1TB disks for storage. Do you think it will be easy to partition these disks in ext3 and to share them with a Windows system over the network?

Sharing with Windows can be accomplished pretty easily with Samba.  [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605), I used that thread to set it up, also sharing with Linux systems can be accomplished with NFS.  I am currently doing the same with an extra computer I have in my Basement.

---

### Post by mick8985 on 2009-05-06
I'd say definitely just a standard ubuntu install (or mint is fine). You want to have a gui installed on the server that way you can use vnc to access the full gui from your windows lappy.
[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")
As previously stated you're going to want to use Samba for file sharing. You mention streaming, if you want to stream music or video from your file server to a client application on windows (or console such as ps3 and xbox360) I'd recommend using a UPnP server such as mediatomb.
[http://xmilk.com/blogs/skgs_ramblings/archive/2007/10/16/test.aspx]("http://xmilk.com/blogs/skgs_ramblings/archive/2007/10/16/test.aspx")
If you want to have your music library streamed to iTunes you should install a firefly (mt-daapd) server
[http://www.oreillynet.com/xml/blog/2004/12/streaming_itunes_from_ubuntu.html]("http://www.oreillynet.com/xml/blog/2004/12/streaming_itunes_from_ubuntu.html") 
There is also great ways to setup torrent daemons, nzb daemons for grabbing binaries from newsgroups I could go into if your interested.

---

### Post by mcduck on 2009-05-06
Yes, Ubuntu will be able to do all the tasks you listed.

I suggest you should install the Desktop version, though, as it includes by default more of the things you will want. And it includes a graphical user interface which you will probably find nicer than the command line available on the Server version.. ;)

Both Desktop and Server version are in the end one and the same OS, and have all the same software available. The only difference is what you get on the out-of-the-box install. Desktop install gives you a graphical desktop with all the standard applications and tools, while server version gives you command line interface with the option to install some of the most common server applications during the OS install. Of course you can later on add server software to the desktop version or desktop to the server version.

(THe Server version also uses server kernel, more tuned for use on servers, instead of the generic kernel suitable for all-round use. Both kernels are freely available and installable on any Ubuntu version, although in your use the generic kernel will definitely be a better choice)

---

### Post by mick8985 on 2009-05-06
> **mcduck said:**
> 
(THe Server version also uses server kernel, more tuned for use on servers, instead of the generic kernel suitable for all-round use. Both kernels are freely available and installable on any Ubuntu version, although in your use the generic kernel will definitely be a better choice)

Just to elaborate on that the server kernel is actually XEN kernel which is used for virtualisation, the proprietary nvidia and ati drivers will not work with this kernel.

---

### Post by Steven_S on 2009-05-06
Great info guys, thank you! It is a joy to be welcomed in the Linux world like that - with real assistance :)

While I'm here - does anyone know of a good backup solution that can pull data from the systems I want to back up, and that also can mirror two internal drives (not RAID)?

---

### Post by AlanR8 on 2009-05-06
I run Kubuntu on four of the six machines I have on my home network. My "file server" runs the normal desktop version and I can do everything I want with this configuration.

It's taken me a while to sort everything out, but these days I can do a clean install on a machine and have it fully talking on the network, Linux to Linux and to windows, have it fully multimedia ready including playing DVDs within about an hour of putting the live CD into the tray.

I've used these forums as the source of all my knowledge and can only say thanks to all the members, its a great community and welcome!

---

### Post by Snyper450 on 2009-05-06
You should try the new server version of Jaunty see how it goes?:)

---

### Post by Steven_S on 2009-05-08
> **AlanR8 said:**
> I run Kubuntu on four of the six machines I have on my home network. My "file server" runs the normal desktop version and I can do everything I want with this configuration.

It's taken me a while to sort everything out, but these days I can do a clean install on a machine and have it fully talking on the network, Linux to Linux and to windows, have it fully multimedia ready including playing DVDs within about an hour of putting the live CD into the tray.

I've used these forums as the source of all my knowledge and can only say thanks to all the members, its a great community and welcome!

Any chance we might steal your time for a walk-through on this? ;)

---

