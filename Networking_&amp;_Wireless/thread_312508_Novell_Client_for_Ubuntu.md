---
title: "Novell Client for Ubuntu"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by SuperByelich on 2006-12-04
I was wondering if anyone has been able to get Novell's Linux stuff to work in Ubuntu?  I would like to be able to use it being that I need it for work.  I would like to be able to connect to resources, and be able to change accounts and different objects in Novell.  Like a ConsoleOne or what not.  

Thanks,
Jason

---

### Post by alpacaman72 on 2006-12-08
If anyone has any ideas, I need help with this also to use Ubuntu at school.

I know the novell client is downloadable from the novell website, but I have not been able to install it

There is also an open source Novel Client
[http://novelclient.sourceforge.net/](http://novelclient.sourceforge.net/)

has anyone gotten it to work?

---

### Post by mips on 2006-12-08
You could always try using alien to convert the rpm files.

---

### Post by staverts on 2007-02-17
Many people have converted the rpm and had still NO successs installing the client, as the .sh script looks for rpm's.  Installing all of the rpm's converted to debs, seems to yeild no, or poor results.

---

### Post by e3chaos on 2007-02-26
i'm also looking for a novell client working with ubuntu.. i know there are work arounds to access the servers and what not, but i'm looking for something that replicates/is the same thing...any luck?

---

### Post by jhroadstar2003 on 2007-02-27
I am brand spanking new to Ubuntu. Last night I got my dvd player to work, build essentials etc. etc. Now that I have all the kibbles and bits I need to live. I would like to add the kibbles and bits to work. We have a Novell client at work and am in need of a Novell Client. I only need to log on to the network and use my resources. Does any one know if the SUSE client would work?

Thx!

---

### Post by Hendrixski on 2007-02-27
SuSe is also RPM based.... and quite frankly, I didn't like it very much.

Can you replace the parts of the .sh script that unpackage the RPM to include commands using Alien?  That sounds like it should fix the problem.  When you're done post your changes somewhere so that others can improve upon it.

---

### Post by GratefulDiver on 2007-05-17
I'm still updating packages from an old original Dapper livecd install I did on my play laptop so I haven't quite gotten to the point of putting any work-related stuff in place on it quite yet, but I'm curious.....

For basic file / print services NCPFS isn't cutting it?
[http://packages.ubuntu.com/dapper/net/ncpfs](http://packages.ubuntu.com/dapper/net/ncpfs)
Seems to be available in every distro, not just Dapper..

How about the gui front end NovelClient at Sourceforge?
[http://novelclient.sourceforge.net](http://novelclient.sourceforge.net)

For Groupwise theres a bit of a howto right here at ubuntuforums...
[http://ubuntuforums.org/showthread.php?p=1002121](http://ubuntuforums.org/showthread.php?p=1002121)

Seems to me that from there, ConsoleOne shouldn't be too tough a row to hoe.. - Its mostly java based anyway isn't it? --- But heres an old CoolSolutions howto that may / may not apply anymore.
[http://www.novell.com/coolsolutions/tip/16609.html](http://www.novell.com/coolsolutions/tip/16609.html)


Just curious if anyone from this thread is working out fine now I guess..... ???

---

### Post by BDNiner on 2007-05-18
I am in the same boat. I use a Novell environment at work and would like to have the client installed so that i can take all resource hungry applications off my windows box. I have read the work a rounds for connecting to network shares and all that but i need a little bit more. I would like to install console one and a management software for our firewalls and switches on a linux box. My co worker is a SUSE freak, if i can get this working then i can one up him and forever prove that ubuntu is better for our environment that SUSE.

---

### Post by hsweet on 2007-05-18
Me too.  Somebody should be able to get it running and explain it to the rest of us (dummies?::shock)  

How come Novell does not release a workable client to the larger linux world?  They've kinda embraced the open source thing.   Gets me thinking.. why is it  so much easier to connect  to a Windows server then Novell?

---

### Post by jkorz on 2007-10-30
I did some python hacking and came up with a program that does a very simple contextless mount of a user's home drive given their username and password. It is kind of rough, but working. The project is at [http://sourceforge.net/projects/jkmount](http://sourceforge.net/projects/jkmount). You need to check it out from subversion and run install.sh. After that, change the config files in /etc/jkmount to reflect your ldap proxy user and enter hostnames and ip's for your servers. You can even specify more than your home drive to mount in ~/.jkm/options. It does not work out of the box with gutsy, ncpfs is broken in the gutsy repo. Ncpfs and libncp need to be downgraded to the feisty versions in the feisty universe repo.

---

