---
title: "Firewall for Linux"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by chris1neji on 2010-03-14
First of all i want to say i did tried linux before like 3yrs or so. i QUIT because i couldnt get youtube to work because i couldnt install the ____ flash player!
 So i was going trough all my favorite websites on one of them firefox pop up saying "missing plugins and ect" and kaboom youtube working after that!!!!

RIGHT NOW I AM HAPPY!!!!:D:D:D

Anyways i am in need of a firewall for linux. I dont care how far or superior or how much more advance a OS is i still care to be protective. I want a firewall. Still deciding weather i should trade off performance for an anti virus and anti spyware program. I know Linux is well known for it's security and that most security software is consider "useless" since the likelihood of having a malicious code is rare. 


Would someone out there please tell me which i should get. Or why they strongly disagree with me. Maybe ... prove me that i really dont need a firewall at all? :O ?

also i wanna chat ... about linux how do i starta  chat irc ? and stuff

---

### Post by mcduck on 2010-03-14
The default install of Ubuntu has no running services that would listen for incoming network connections, so there really isn't anything for a firewall to do. You only need to set up a firewall if you install some server application and whnt to restrict access to it in more detailed way than the apps own configuration allows, or if you want to limit what sites the users of your system can access.

But if you still want to set up a firewall, use UFW (Installed by default) or install Gufw if you want a graphical tool.

What comes to antivirus apps, those only scan for Windows viruses. And I don't really think there even is an antispyware app for Linux, I've never heard of an malware for Linux... :D

I'm not really interested in convincing you to not install any of these things, since it's a topic that has been discused again and again so many times you should easily find more detailed information about it than anybody cares to type to forum posts any more. I'm just telling you that you *don't need* any of those programs. :D

---

### Post by chris1neji on 2010-03-14
Thanks for replying i have always heard that Linux does not need security software i however was thinking of a firewall in a way it works on windows. How information works and how firewall is your first line of defence, to protect yourself against any potential harmful malicious coding. Then there is also the second part to block certain programs and such.

---

### Post by Tikkyca on 2010-03-14
I have installed firewall from this page:
[http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html](http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html)

---

### Post by J V on 2010-03-14
A firewall is to stop something getting in, or stop a specific program from getting out.

Nothing is listning by default, unlike windows, so the first is not needed. And permissions should take care of the latter

There are only 40 linux virusses, of which *mabey* one is in the wild, but it would take a lot of work to get running, please see my pre-made posts :)

> **Viruses**
Linux has almost no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If there ever was a serious Linux virus out there, to get it to actually work, you would need to:


[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]

 On windows, all you have to do is to log onto your email, windows does the rest automatically, which leaves you open to viruses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

**Firewall**
Ubuntu comes with a fantastic firewall known as iptables. It is inactive by default, because no applications are "Listening" to the ports (Doorways) on your computer anyway, so there is no need for a firewall.

Iptables is actually very hard to configure, you need to edit configuration files, know the program, its just much more advanced. Luckily, there are tools that make this easy.

The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.

---

### Post by presence1960 on 2010-03-14
open a terminal and run ```
sudo ufw enable
```

If you want a GUI for that in terminal run ```
sudo apt-get install gufw
``` Once installed you can access it from System > Administration > Firewall configuration

I suggest you read this for more info on security in ubuntu. Forget the windows mentality: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by gdonwallace on 2010-03-14
At my work we run several Windows machines, so we have to have a machine running a Firewall.  We are running a program called Shorewall.  Not sure how much control you are looking for.  We have a machine dedicated to our firewall.  In the 3 years that I have been there, the only problem that we have had has been that someone has brought in a virus on a USB stick.  

I can check it every morning to see what has been attempting to get in, and every time I see that the firewall has been pinged, but nothing has been able to get through.  

Shorewall is a full on firewall.  There may be varients of it that you can run for personal use; I just don't know.

Good luck.

---

### Post by boxcorner on 2010-03-15
When I first installed Ubuntu, I started by reading New to Ubuntu? Start here... > Free Ubuntu Pocket guide by Keir Thomas.  He recommended Firestarter, which I installed. It seemed to work fine.  However, I have had problems with Firestarter since I re-installed Ubuntu.  Furthermore, clicking on Help > Online Users' Manual doesn't work and clicking Help > Firestarter Homepage results in a page not found error.  Google search for Firestarter similarly results in the same error. Perhaps someone could add a note to New to Ubuntu? Start here... advising newcomers to install gufw, rather than firestarter.

---

### Post by Brv on 2010-03-15
Ubuntu is pretty secure by default, I believe It's fairly secure by default but I have been 2 years with still default.. Without GUI Firewall.

---

