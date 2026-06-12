---
title: "Downloading and installing NONE Synaptic packages..."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-23
I was wondering if someone could tell me a little more about how to do this? I read something in this forum about command line. What is that? If I do download something from the internet, How can I check it for viruses and such? What is the best way to download something from the net? and one last question for this post...Someone once posted a link and for the life of me I can't remember it, but a link for how to's in ubuntu, I think. Could someone post it again for me Thanx...

---

### Post by albinootje on 2009-01-23
> **Leo Dragonheart said:**
> I was wondering if someone could tell me a little more about how to do this? I read something in this forum about command line. What is that? 

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
> 
If I do download something from the internet, How can I check it for viruses and such? What is the best way to download something from the net? 

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
> 
and one last question for this post...Someone once posted a link and for the life of me I can't remember it, but a link for how to's in ubuntu, I think.

Here's a good start : 
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by Muffinabus on 2009-01-23
The absolute best way to download programs for Ubuntu is to use the Synaptic package manager.  You should always check this first to see if your desired program is in the repositories (it's like a list of programs).  You can access it by going to System > Administration > Synaptic Package Manager.  It will ask for your password, just input it there, and you'll see a search box so that you can search for your program.

You can also install programs from the Terminal (or command line) which can be accessed by going to Applications > Accessories > Terminal.  To install stuff here, say you wanted to install wine, you would type ```
sudo apt-get install wine
```.

---

### Post by Leo Dragonheart on 2009-01-23
That is perfect...Thanx for the links...and the sudo apt-get install ...info.

---

### Post by RomeReactor on 2009-01-23
Hi. The command line is, as you may know, the text based interface; you can use the terminal (Applications->Accessories->Terminal) to issue commands, such as installing packages with command-line package managers such as aptitude or apt-get.

As Muffinabus says, it is recommended that you install packages from the official repositories to avoid security risks, since installing programs requires the administrator password. If you decide to go ahead and install programs not found in the repositories, you can get .deb packages from [GetDeb]("http://www.getdeb.net"). If the program you're looking for is not available there, or is not available as a .deb packages from the site you download it, you would probably download an archive (.tar.gz, zip, etc) and you'd have to use the terminal to install it. The particular method of installation depends on what the contents of the archive are, and usually there's a readme file inside detailing the procedure.

And then there are some downloaded programs that you don't need to install; you just extract the contents of the archive and double-click on the executable.

---

