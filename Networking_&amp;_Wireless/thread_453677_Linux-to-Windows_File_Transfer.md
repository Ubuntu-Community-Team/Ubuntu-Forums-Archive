---
title: "Linux-to-Windows File Transfer"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by ceci123 on 2007-05-24
hi,

recently i installed ubuntu on  my new work pc. 

I now need to transfer all my files from my xp machine to my new Ubuntu machine. 

I am newb at this....pls help. I did some google search but none seem very helpful. 

thank you!

c.

---

### Post by tgm4883 on 2007-05-24
A couple different ways you could do this.

1.  Setup Samba (the windows file sharing protocol)
2.  Setup a ftp server (another protocol used for transfering data)
3.  Burn it to a disk and use sneakernet (probably the easiest)

---

### Post by benanzo on 2007-05-24
Are both these machines on the same network?  You could just put your files in a shared folder on XP and then copy them from Ubuntu.  Or you could burn them to a CD/DVD and transfer them.  If you have an external disk you could use that.

---

### Post by ceci123 on 2007-05-24
Yes. i am on the same network. 

I like the idea of "You could just put your files in a shared folder on XP and then copy them from Ubuntu". But how?

I don't want to burn into CDs for many reasons. I would like to know how to do it without burning into CD/DVDs. 
I don't mind getting my hands dirty but I need some direction.

When i type the following command
"sudo aptitude search ftp"
it tells me that an The FTP client is installed. 
But I also noticed that there is a "ftp-server" available for installation. If I install this "ftp-server" will i be able to transfer those files?

Thank you.

c

---

### Post by tgm4883 on 2007-05-24
Make a shared folder in Windows XP.  (Probably right click on the folder and click on sharing if memory serves me)  Then browse the network from ubuntu, find the shared folder, and drag and drop

---

### Post by ceci123 on 2007-05-25
I think i am now able to transfer the files from windows to ubuntu. 

I just installed ftp server on ubuntu. Then installed SSH Secure Shell on my windows machine. 
From windows XP I just connected to my ubuntu through SSH Secure Shell. Once connected I just uploaded all the files. 

c

---

### Post by ruy_lopez on 2007-05-25
People should pay attention to what tgm4883 posts above. Telling people to use Samba, when using Windows sharing would do, isn't the best of advice. A lot of people will find Samba has a non-trivial configuration. Using Windows sharing, and then browsing the network with Places --> Network, is still technically using samba (the client version). But when you tell people, "use samba", without telling them the easy method, they go and read all the Howto's and end up bogged down in samba server configuration problems. Then they end up here again, saying, "how do I configure samba."

---

### Post by tgm4883 on 2007-05-25
> **ruy_lopez said:**
> People should pay attention to what tgm4883 posts above. Telling people to use Samba, when using Windows sharing would do, isn't the best of advice. A lot of people will find Samba has a non-trivial configuration. Using Windows sharing, and then browsing the network with Places --> Network, is still technically using samba (the client version). But when you tell people, "use samba", without telling them the easy method, they go and read all the Howto's and end up bogged down in samba server configuration problems. Then they end up here again, saying, "how do I configure samba."

Calling me out huh?  I posted setup Samba because I wanted him to setup Samba (hence why I said, Setup Samba).  This however, is because I had forgotten that Samba needed no setup for this type of application, a mistake on my part.  I would have went into further detail but I figured that more explanation wasn't needed since this isn't the absolute beginners forum (although another mistake on my part as a little searching in the community docs would have brought up the [ComprehensiveSambaGuide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide") which explains just what you want him to do)

As for Samba setup being a pain, it really is.  That is if you don't use something like SWAT or Webmin.

---

### Post by ruy_lopez on 2007-05-25
You know what, samba isn't really that hard. But the problem is that most people who NEED samba, have just migrated from Windows to using Linux for the first time. Having their first experience of Linux by wading through the smb.conf isn't the best way to make sure they don't switch straight back to windows.

---

### Post by dannyboy79 on 2007-05-25
the easiest way would be to use cifs and mount your windows shared drive within your ubuntu install adn then simply copy and paste from Nautilus. here's a guide for cifs fstab entry. [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
(NOTE: just follow the fstab entry info and the info about installing smbfs BUT dmizer's explaination that you have to install winbind is NOT true, nor do you have to change your nsswtich.conf because there is more than one way to resolve names in a mixed environment- See here: [http://ubuntuforums.org/showthread.php?t=391601&highlight=resolve](http://ubuntuforums.org/showthread.php?t=391601&highlight=resolve))

PS (Samba is not hard at all to setup once you understand what you're doing with it and why. I have only been in linux for a little over a year and I  read thru man smb.conf. You'll then understand it in no time and not just listen to how "other" people got  it to work and instead you'll set the things that you want for YOUR setup.)

---

### Post by morningboat on 2007-06-16
Yes, Samba's configuration may drive new converters back to windows since they have used to the GUI admin. What I'd suggest is that FTP solution (with the GUI admin) is a safer and easier way for them to transfer the files. 

In my opinion, the best solution should be a free cross platform GUI FTP Server and Client so that they can check it on either platform before they try to migrate. Hence I'd recommend CrossFTP [Server]("http://www.gnomefiles.org/app.php/CrossFTP_Server") and [Client]("http://www.gnomefiles.org/app.php/CrossFTP_Client") for them, which runs on either platform with nice GUI, and is extremely easy to use as well. Its site has [a CrossFTP Server install guide]("http://www.crossftp.com/server_guide.htm"), and normal person can easily install and configure the server within 5 minutes if following the guide. People should recommend such tools to newbies.

---

### Post by tgm4883 on 2007-06-16
Whats with people digging up month old threads today?

---

### Post by dannyboy79 on 2007-06-18
> **tgm4883 said:**
> Whats with people digging up month old threads today?

it's way better than starting a new thread for the same thing!

---

### Post by tgm4883 on 2007-06-18
> **dannyboy79 said:**
> it's way better than starting a new thread for the same thing!

I could understand it if they were asking the same questions (although not for the few threads that I have seen dug up from 2 years ago).

But some people are digging up threads that have been answered just so they can post their answer too. (Which is usually the same as previous posts.)

---

