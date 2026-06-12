---
title: "Need help creating repository DVD's"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by flit on 2009-01-01
Hello,

I was following instructions to create a Ubuntu repository DVD,
I downloaded the packages [like 30GB] already but I got stuck
because I could not install debpartial to divide the packages
into DVD-sized portions. Can anyone help me with this issue?
Is it possible to setup a offline web server with the packages
on it and add it to sources.list? Would that work?
Thanks in advance.

---

### Post by namdung on 2009-01-01
I'll not be able to help u with the DVD but u may create a local web repository for sharing the downloaded resources using *apt-mirror*

The steps to follow:
1. ```
sudo apt-get update
```

2. Install apt-mirror ```
sudo apt-get install apt-mirror
```

3. By default the mirror is saved in */var/spool/apt-mirror*. This can be changed to any other place including external USB drive.
```
sudo gedit /etc/apt/mirror.list
```

4. Create repository ```
sudo apt-mirror /etc/apt/mirror.list
```. This usually takes a long time depending on the Internet bandwidth.

5. Install Apache server to make the local repository accessible over http
```
sudo apt-get install apache2
```
The default Apache document root under Debian and Ubuntu is */var/www,* create the symlinks */var/www/ubuntu* that point to the real repositories
```
sudo ln -s /var/spool/apt-mirror/mirror/in.archive.ubuntu.com/ubuntu /var/www/ubuntu
```

6. Change the sources.list to point to the new repository server for updates.
```
sudo gedit /etc/apt/sources.list
```

7. To keep your mirror updated activate the cron entry in /etc/cron.d

For more details:
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)
[http://odzangba.wordpress.com/2007/12/24/use-apt-mirror-to-create-your-own-ubuntu-mirror/](http://odzangba.wordpress.com/2007/12/24/use-apt-mirror-to-create-your-own-ubuntu-mirror/)
[http://ubuntu-tutorials.com/2008/06/10/how-to-create-an-ubuntu-repository-mirror-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/06/10/how-to-create-an-ubuntu-repository-mirror-on-ubuntu-804/)

---

### Post by k3lt01 on 2009-01-01
Check out BobSongs excellent [How To: Make Your Own Ubuntu Repository DVDs]("http://ubuntuforums.org/showthread.php?t=352460"). I have personally used this and can vouch for its accuracy.

---

### Post by hyper_ch on 2009-01-02
you should not double post!

---

### Post by flit on 2009-01-05
Thanks for the replies. 

Sorry for the late reply, and sorry about the double post, this was my first
post and when I submitted the post, I received an error message and
I thought that it wasn't posted. So I submitted the post again, and
I don't know how to delete a post. 

hyper_ch thanks for the tip, I did not know about aptoncd. I got no Internet connection, I am using my friends connection. I just want to be able to install Ubuntu software when I am offline.

---

