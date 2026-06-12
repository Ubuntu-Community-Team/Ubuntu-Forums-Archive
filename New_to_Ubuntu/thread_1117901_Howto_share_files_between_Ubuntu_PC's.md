---
title: "Howto share files between Ubuntu PC's"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-04-06
Hi All

I have just installed jaunty onto my wifes laptop,removing Vista in the process.   :lolflag:

With the old setup i shared files using Samba Shares between my Intrepid and her Vista.

Can i still use Samba for Ubuntu to Ubuntu ?

Or any suggestions will be gratefully received.

Thanks

Clive

---

### Post by Cybie257 on 2009-04-06
Simple Answer: YES. :)

If you have already successfully used Samba from Vista to Ubuntu, then you should have the basics down. Just install/setup Samba in the new install and add the user (smbpasswd -a <username>) and you should be good to go. 

-Cybie257

EDIT ADD: Since you installed Jaunty, if you have any issues connecting, go into Synaptics and reinstall the installed Samba Packages and try again. I've had to that with 2 computers for some odd reason. I also suggested it to another user and seemed to fix his problems also. Might be something that breaks with updates????

---

### Post by linux_lover69 on 2009-04-06
Right click on a folder you want to share and then click on properties, then click on share folder.

---

### Post by billgoldberg on 2009-04-06
Don't use Samba to share files between Ubuntu computers.

Samba is meant to connect Linux with Windows, not Linux with Linux.

Sure it's possible, but not really advised to do.

Use SSH instead, I've written a little how-to on my blog a while back.

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

---

### Post by clive littlewood on 2009-04-06
Thanks All

I will try the Samba route as this is the easiest !!

Thanks for the link Bill i will give this a go if Samba fails.

Clive

---

### Post by billgoldberg on 2009-04-06
> **clive littlewood said:**
> Thanks All

I will try the Samba route as this is the easiest !!

Thanks for the link Bill i will give this a go if Samba fails.

Clive

SSH is way easier to set up that Samba.

Just run 

sudo apt-get install ssh 

and you are done.

Now you can connect to all the pc's that have ssh installed on your network using "Places -> Connect to server".

---

### Post by stchman on 2009-04-06
> **clive littlewood said:**
> Hi All

I have just installed jaunty onto my wifes laptop,removing Vista in the process.   :lolflag:

With the old setup i shared files using Samba Shares between my Intrepid and her Vista.

Can i still use Samba for Ubuntu to Ubuntu ?

Or any suggestions will be gratefully received.

Thanks

Clive

Forget Samba, NFS is a far better sharing option for Linux to Linux boxes.

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

Alternately you can use ssh.

---

### Post by wylfing on 2009-04-06
I support the nominations of NFS and SSH as better alternatives than Samba. Although Samba is a great piece of software, it is very finicky (largely I suspect because Windows is intentionally difficult to connect to, to keep non-Windows computers from interoperating).

NFS involves a very short learning curve, probably less than Samba. SSH is extremely easy.

---

### Post by MockY on 2009-04-06
The drawback of SSH is that due to encryption, it makes the transfer a tad slower. And since you are sharing within the LAN, there is no reason to use encryption. But yes, SSH is very easy to use and I use it whenever I don't have to send huge files or a large quantity of files.

---

### Post by clive littlewood on 2009-04-07
Hi All

Thanks again for all the replies.

The solution I have found is an app called "Giver" which is in the repos.

Install on each computer and when you start giver the available shares appear  on your list.

Just drag and drop your file or foto to the person on the list you want to share with.

A popup message appears on their desktop asking if they wish to accept the transfer.

If they accept then the transfer takes place and you receive a popup informing you of the acceptance.

A very simple but brilliant program.

The app was a product of the Google summer of code program an if you google Giver you can watch a video demo of the program.

I hope this solution helps others.    Try it      :p



Regards

Clive

---

### Post by MockY on 2009-04-07
The problem with this app however, is that the files shared must be accepted. You can't in other words just send files without anyone on the other end. This is an assumption though since I have never used this app. But if I'm right, Giver is not a good NFS, SSH, Samba alternative. 
It sure is a great LAN Party software, but it's very unlikely we'll ever see the day when everyone at a LAN party is using Ubuntu. But awesome that you found a solution that fit you.

---

### Post by Fenris_rising on 2009-04-07
> **billgoldberg said:**
> Don't use Samba to share files between Ubuntu computers.

Samba is meant to connect Linux with Windows, not Linux with Linux.

Sure it's possible, but not really advised to do.

Use SSH instead, I've written a little how-to on my blog a while back.

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

Used by me thanks for the blog ;)

regards

Fenris

---

### Post by ranch hand on 2009-04-07
billgoldberg
I have to thank you for this.

I am not having any luck setting up a nfs network at all (I think I installed everything I need but the right files are not there).

SSH seems to have done what I needed to do anyway.  That took me more than 2 minutes though.  I bet it took 5 to download to both boxes and use.

Thanks again

---

### Post by R_U_Q_R_U on 2009-05-03
> **billgoldberg said:**
> SSH is way easier to set up that Samba.

Just run 

sudo apt-get install ssh 

and you are done.

Now you can connect to all the pc's that have ssh installed on your network using "Places -> Connect to server".

Super Excellent - SO EASY.

THANKS!

---

### Post by VastOne on 2009-05-04
> **R_U_Q_R_U said:**
> Super Excellent - SO EASY.

THANKS!

Ditto!

---

