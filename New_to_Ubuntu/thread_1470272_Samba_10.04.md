---
title: "Samba 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by randumnumber on 2010-05-02
I just installed Samba on 10.04 I didn't use a command line install i just clicked sharing options and it asked me if i wanted to install samba i said yes. I am trying to share my Videos folder over the network to my laptop running ubuntu 9.04. But i am getting:

Unable to mount location
Failed to retrieve share list from server

as an error message.
I am using the default configuration file, all im doing is right clicking the videos folder and sharing options > share this folder> allow other people to write and guest access.

I am using a clean install of 10.04 with a LAMP server installed on it. I dont know if this would get in the way, but i had the exact same setup on the machine when i had 9.04 installed and it worked fine. 

Some weird things are going on like when i attempt to use 
```
sudo /etc/init.d/samba restart
``` it says the path doesnt exist, so i check and used
```
sudo /etc/init.d/smbd restart
``` and get
"Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart smbd
smbd start/running, process 2173"
so i used
```
service smbd restart
```
and get a 
smbd start/running, process 2182


Is this normal? 

When i am using 9.04 i can use the init.d script and get a proper output of stop deamon and start deamon ok

One more weird thing, on my laptop running 9.04 i decided maybe i should copy the smb.conf file to my 10.04 box to see if it would work and found something weird...

i have the Music folder shared on my laptop and it works fine, but in the smb.conf file there is no reference to Music or the path to my Music folder....so how does it know where my Music folder is?!!! is it storing this information somewhere else?

Any input on what i can do?

I have tried reinstalling samba to no avail, i have tried putting the path to the folder in the smb.conf file manually to no avail. 


help?

---

### Post by LasloHollyfeld on 2010-05-04
I probably won't be of any help, but I'm curious about what your output is from:

dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba

At least you'd be able to know that all the right packages installed completely / correctly.

---

### Post by phenexfire on 2010-05-10
It looks like that is normal output, I am also running a clean install of 10.04 with a few things installed. I used sudo service smb stop to see what it would tell me and the result was:
```
shawn@Macbuntu:/etc/samba$ sudo service smbd stop
smbd stop/waiting
shawn@Macbuntu:/etc/samba$

```

and then when I restart it:
```
shawn@Macbuntu:/etc/samba$ sudo service smbd start
smbd start/running, process 1859
shawn@Macbuntu:/etc/samba$
```

My problem is of course the same as the poster. Initially I shared a couple of folders after adding the share details to the smb.conf file but it would not let me use any credentials to log into it. So the next thing I have tried is backing up the original smb.conf and creating a simple version but even this so far asks for credentials and does not allow me in.

here is the output when I run the query from Laslo.. nice to see you still out of the basement Laslo! =)

```
shawn@Macbuntu:/etc/samba$ dpkg-query -W -f='${Package} ${Version} ${Source} ${Status}\n' | grep samba
libsmbclient 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
libwbclient0 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
samba 2:3.4.7~dfsg-1ubuntu3  install ok installed
samba-common 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
samba-common-bin 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
smbclient 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
smbfs 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
winbind 2:3.4.7~dfsg-1ubuntu3 samba install ok installed
shawn@Macbuntu:/etc/samba$
```

---

### Post by phenexfire on 2010-05-11
:) Bump

---

### Post by phenexfire on 2010-05-12
In case this is of interest to anyone else, after reading some threads about others trying get file sharing working I replaced the original smb.conf with only the workgroup changed to reflect where it needed to be and to allow sharing of any folders regardless of owner I then went into the file browser and used the sharing option on the right click menu. That actually worked and I was able to access the folders I shared without fail. 

I should have tried that first but as they say, you make a simple problem more complicated by over analyzing it. So maybe that will work for someone else. good luck.

---

### Post by tad1073 on 2010-05-12
you probably need to edit you /etc/samba/smb.conf file to reflect your work group

---

### Post by phenexfire on 2010-05-12
> **tad1073 said:**
> you probably need to edit you /etc/samba/smb.conf file to reflect your work group

let me clear that up.... I put the original smb.conf back with the workgroup specified. =)

---

