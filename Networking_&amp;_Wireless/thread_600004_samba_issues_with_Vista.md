---
title: "samba issues with Vista"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by hexcentric1 on 2007-11-01
Ok, let me describe the simple issue: Vista machine can access samba share on linux box, but linux box cannot access Vista share on Vista machine.

The details:
Linux box is running Xubuntu 6.10, wireless home network. Vista machine is on same wireless network, also wireless.

```
me@blah:~$ smbclient -L //VISTA-PC
Password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6000] Server=[Windows Vista (TM) Ultimate 6.0]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows Vista (TM) Ultimate 6000] Server=[Windows Vista (TM) Ultimate 6.0]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

```
me@blah:~$ sudo smbmount //VISTA-PC/share ./VISTA/
Password:
me@blah:~$

```

which looks good (the second part) but then nothing happens.

```
me@blah:~$ ls VISTA
ls: VISTA: Permission denied
me@blah:~$ sudo ls VISTA
ls: VISTA: Permission denied
me@blah:~$ 

```

strangely enough:

```
me@blah:~$ mount
...
//TRIXY-PC/share on /home/me/VISTA type smbfs (rw)
me@blah:~$ 

```

alternate solution also does not work:

```
me@blah:~$ sudo mount -t cifs //VISTA-PC/share /home/me/VISTA -o guest,domain=WORKGROUP,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
me@blah:~$ 

```


what i've tried so far:

supposedly, samba and vista don't like each other because of this:
[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

well, first of all i'm running samba 3.0.22, which should work with NTLMv2, and second i changed the Vista settings per the link above. still no dice. 

The share folder on the Vista machine is set to open sharing, no authentication required. the samba config is set to security=share

i've also tried everything above, but replacing VISTA-PC with the ip address, that has no effect at all.

any assistance/insight would be greatly appreciated, thanks in advance

---

### Post by froy02 on 2007-11-02
See this link for answer.

[http://ubuntuforums.org/showthread.php?t=598887](http://ubuntuforums.org/showthread.php?t=598887)

---

### Post by froy02 on 2007-11-02
Sorry I misdirected you on my last post.  You have to allow file sharing on the VISTA machine for Ububtu to see your share.  Click on Start > Computer> Netwok.  On the menu bar click on Netwok and Sharing Center. A dialog box would open.
Go to the Sharing and Discovery at about the middle pane.
You would see these:

Network Discovery  
File Sharing
Public Folder sharing
Printer Sharing
Password Protected Sharing
Media Sharing
Turn them  first 4 ON or OFF whichever you want to allow.

Here is my setup:

Network Discovery  = ON
File Sharing             =ON
Public Folder sharing=ON
Printer Sharing         =ON
Password Protected Sharing =OFF
Media Sharing           =OFF

---

### Post by hexcentric1 on 2007-11-05
yes, i have Vista set up for sharing. it should be working, but its not

---

### Post by samosamo on 2008-04-11
I am having the same issue.  Didn't think a new thread was necessary.

---

### Post by Eiríkr on 2008-04-11
I've read elsewhere that Vista includes a new version of the CIFS (i.e. Samba) sharing engine that has rather severe compatibility issues with anything non-Microsoft (surprise, surprise).  Enough people complained that apparently SP1 is supposed to include fixes.  If you haven't installed SP1 yet, you might want to try installing it (back everything up first!), and then see if your Linux machines can access the Vista shares.  

Cheers,

Eiríkr

---

