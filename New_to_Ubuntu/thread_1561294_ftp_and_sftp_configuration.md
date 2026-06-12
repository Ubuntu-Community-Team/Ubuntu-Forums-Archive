---
title: "ftp and sftp configuration"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by mail2vs.dvg on 2010-08-26
Hi,

I am trying to make ftp and sftp connection between ubuntu 10.04 desktop and windows xp. 
I am using ultraedit in windows to access the linux hard drive and also access the external hard
drive which is connected to ubuntu linux.

So how can i configure ftp and sftp in ubuntu 10.04 desktop? 
Please provide me configuration settings.

Thanks,
mail2vs.dvg

---

### Post by Peter09 on 2010-08-26
There are several ftp servers available within the repositories, you'll need to install one if you want to use the Ubuntu machine to serve files through ftp.
 
For sftp install open-ssh (Ithink thats what its called). Its the server side of ssh.

---

### Post by lkraemer on 2010-08-26
As Peter09 stated, you need a Server running on one machine, then you need
the Client software running on all machines accessing the server.  Mixing
M$ with Linux machines shouldn't be a problem....

There is good information on the FreeNAS Forum, KB, and SUG about how to
access each type of Server you are asking about.  Check out Sections 2.6.x
and 6.x for the Setup Information and Howto use these services.  I'd recommend
using SFTP or FTPES over TFTP.  Also, if your local on the LAN,
you might want to try NFS as it works wonderful.  (I just wouldn't use
NFS over the Internet because it wouldn't be secure....)  

CIFS (Samba) works well and is the M$ Default.

REF:
[http://sourceforge.net/apps/phpbb/freenas/index.php?sid=957a41b87a8f4b796f281ff81c0858d2](http://sourceforge.net/apps/phpbb/freenas/index.php?sid=957a41b87a8f4b796f281ff81c0858d2)

[http://freenas.org/documentation:setup_and_user_guide](http://freenas.org/documentation:setup_and_user_guide)

[http://www.freenaskb.info/kb/](http://www.freenaskb.info/kb/)

Once you read this documentation you should be able to apply it to your
setup.  Or you could set up a FreeNAS System and use that......Good Luck!

lk

---

