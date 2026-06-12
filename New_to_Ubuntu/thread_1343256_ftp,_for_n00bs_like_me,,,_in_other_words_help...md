---
title: "ftp, for n00bs like me,,, in other words help.."
date: 2009-12-01
forum: New to Ubuntu
---

### Post by beanco on 2009-12-01
so,

sitting at home and I need to get several files on to the network where i work....

yes, I could email them each, but there has to be a better way... right?

that would be FTP, right?

Thanks.


Robi

---

### Post by Zzl1xndd on 2009-12-01
Do they have an FTP server set up?

If so most web browsers are able to handle FTP, although I prefer a program like Filezilla.

Normally you would need to know the address of the server, and have login credentials.

---

### Post by sandyd on 2009-12-01
> **beanco said:**
> so,

sitting at home and I need to get several files on to the network where i work....

yes, I could email them each, but there has to be a better way... right?

that would be FTP, right?

Thanks.


Robi
some networks at offices have a VPN service that allows you to connect to their network remotely.
p.s. could use hamachi for that
p.p.s. as a second thought, FTP will not work because you are sharing the same ip address (WAN) with all of the computers on your network. you will need to explicitly route the ftp port through the router and i dont think your network admin will like that.
p.p.p.s. hamachi is actually the best option for you. its easy and doesnt require much configuration. i can walk you through the installation steps if you want.

---

### Post by Some Penguin on 2009-12-01
There are multiple possible ways.  Loosely, they group into three cases:

1) one machine is server for some process, one machine is client  

Both machines are likely to be behind routers rather than directly connected to the internet.  If a virtual private network is not being used... the router on the server's network must have port forwarding set up so that an incoming connection can be routed to the server; in addition, the port and protocols to be used must be let through the firewall.  This is not necessarily possible at your work place unless you control the network, or buy a sufficient number of beers for a trusting network administrator. 

If it is possible, you have your choice of protocols.  ssh has a file transfer client (sshd on server, scp on client) and can transfer either way.  An FTP daemon can be set up on the server.  SSH may be fractionally simpler since sshd is more likely to already be set up.


2) Both machines are clients; you use a third-party service.  For instance, Dropbox (which allows 2GB for free accounts).  There are hordes of third-party filehosting services, many of which offer a couple of GB for a completely free trial, and which generally these days offer a web-based interface.  This can be simple (little setup on your part, no fiddling with router configs) but might be slow.  Some of these offer clients which automatically synchronize a local folder with the shared folder -- convenient if you want to do this frequently.  You should probably clear this with your network administrator if that's what you are doing.


3) Sneakernet.  A flash drive holding 8GB ain't expensive these days.  Requires physical access and relevant ports to both machines (may be a policy violation at particularly security-conscious workplaces, incidentally).  Use a filesystem understood by both -- e.g. FAT16, FAT32 and NTFS are likely to both be supported unless you're using something very old or exotic.  Don't remember what filesystems Irix and OSF support, but you're almost certainly not using either at work.

---

### Post by beanco on 2009-12-02
as usual I left some info out of my OP.

I use Epiphany as a browser, not sure how to FTP with that...



I know the ftp address and I have the rights to use it, log on whatever.... 

Actually, I would not mind knowing how to do this from the command line, if that can be done at all,... rather than using a browser....

thanks

robi

---

### Post by BDNiner on 2009-12-02
To use your browser you can just type [ftp://x.x.x.x](ftp://x.x.x.x) (whatever the address if that you are trying to connect to) and you will be prompted to login and be able to browse the ftp share.

The use ftp from the command line:
1. Type ftp and enter to continue.

2. Type open and enter to continue.

3. Type ftp server ip address and enter to connect to ftp server.

4. If connected, type login name and enter.

5. Type user password and enter. If the username and password are valid, then you'll be in.

site where all this information was obtained and more:
[http://linuxservertutorials.blogspot.com/2008/11/ubuntu-linux-ftp-command-line.html](http://linuxservertutorials.blogspot.com/2008/11/ubuntu-linux-ftp-command-line.html)

---

### Post by ukripper on 2009-12-02
use ubuntu one - [https://one.ubuntu.com/](https://one.ubuntu.com/)

Second better option for documents use Gspace extension with firefox and upload it on to your gmail account. [https://addons.mozilla.org/en-US/firefox/addon/1593](https://addons.mozilla.org/en-US/firefox/addon/1593)

---

### Post by ikt on 2009-12-02
> **ukripper said:**
> use ubuntu one - [https://one.ubuntu.com/](https://one.ubuntu.com/)


or dropbox:

[https://www.dropbox.com/](https://www.dropbox.com/)

Same thing basically, dropbox/ubuntu one are the best thing since sliced cheese imo.

---

### Post by beanco on 2009-12-02
> **BDNiner said:**
> To use your browser you can just type [ftp://x.x.x.x](ftp://x.x.x.x) (whatever the address if that you are trying to connect to) and you will be prompted to login and be able to browse the ftp share.

The use ftp from the command line:
1. Type ftp and enter to continue.

2. Type open and enter to continue.

3. Type ftp server ip address and enter to connect to ftp server.

4. If connected, type login name and enter.

5. Type user password and enter. If the username and password are valid, then you'll be in.

site where all this information was obtained and more:
[http://linuxservertutorials.blogspot.com/2008/11/ubuntu-linux-ftp-command-line.html](http://linuxservertutorials.blogspot.com/2008/11/ubuntu-linux-ftp-command-line.html)


I got it wiht this.... neat stuff... now I just have to figure out how to find actually get the file 
 /robi/tul.ods to the other network...

fun stuff... thanks

robi

---

### Post by beanco on 2009-12-02
> **ikt said:**
> or dropbox:

[https://www.dropbox.com/](https://www.dropbox.com/)

Same thing basically, dropbox/ubuntu one are the best thing since sliced cheese imo.


i am not a fan of sliced cheese but I can see the advantage of sticking stuff on all your various computers at one time...

it kind of makes it seem like ftp is just old fashioned, even out dated.....

robi

---

### Post by Some Penguin on 2009-12-02
> **beanco said:**
> I got it wiht this.... neat stuff... now I just have to figure out how to find actually get the file 
 /robi/tul.ods to the other network...

fun stuff... thanks

robi

Usually, there are commands 'get' / 'put'.  I'll note that there's also usually a command to specify 'binary' mode, which tends to be a good idea to invoke if it's not being used by default.

---

### Post by beanco on 2009-12-02
I tried those commands but it did not work... i will try to reproduce the error msg and post it here.

robi

---

### Post by beanco on 2009-12-02
i managed to use ftp by going to places - conect to server and figuring out what to put inwhicdh flied... yeha, it was easier, much easier than I thought...

but it did leave an ftp as  XYZ on ftp.pol.hu folder.... not sure why....

I tried it from the CL too but that did not work out....

I tried using put but in the end I always got an error about the local file not existing or sg like that... so just what do I need to write if

1. the file i need is fufu on my desktop

2. I need to put it on ftp.pol.hu on drive H in folder rob

Thanks

Robi

---

