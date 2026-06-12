---
title: "library installed but cannot used."
date: 2009-03-14
forum: New to Ubuntu
---

### Post by wssoh85 on 2009-03-14
Hi all,

I'm using Ubuntu 7.10.
I have an application that require the pjlib. So i download the tar ball of the pjlib. after all going smooth, and the sudo make install is done, I try to run my application again. However, is seem like the library not yet being install. Then I go to check it out my /usr/local/include folder and found that the require header is all read but all their permission to access is set to "none". I wondering that those permission should be set to "read only" right? 

Then mine another Ubuntu 7.10 box is also doing the same thing but those header file in /usr/local/include are all "read only". Is any one can help me with this?

thanks

regards,
ws

---

### Post by taurus on 2009-03-14
After installing new libraries, did you remember to run

```
sudo ldconfig
```

---

### Post by wssoh85 on 2009-03-14
Hi, I just try to type "sudo ldconfig" after installation but seem like it do nothing. Can you tell me what is the sudo ldconfig is used for?

---

### Post by taurus on 2009-03-14
Which application/program are you trying to run?  Is it something that you built from source?  Go to the directory where that app is and run this command to see what's missing on the list.

```
ldd program_name
```

```

NAME
       /sbin/ldconfig - configure dynamic linker run time bindings

SYNOPSIS
       /sbin/ldconfig  [ -nNvXV ] [ -f conf ] [ -C cache ] [ -r root ] direc-
       tory ...
       /sbin/ldconfig -l [ -v ] library ...
       /sbin/ldconfig -p

DESCRIPTION
       ldconfig creates the necessary links and  cache  to  the  most  recent
       shared  libraries  found  in  the directories specified on the command
       line, in the file /etc/ld.so.conf,  and  in  the  trusted  directories
       (/lib  and /usr/lib).  The cache is used by the run-time linker, ld.so
       or ld-linux.so.  ldconfig checks the header  and  file  names  of  the
       libraries  it  encounters  when determining which versions should have
       their links updated.

```

---

### Post by wssoh85 on 2009-03-14
Hi, thanks for your reply. 
The application I want to install is modified version of vlc. I have modified the vlc for own using by adding pjsip library to it. So I know that it will require the pjsip library to be install first.

The problem now is when I use command sudo make install for the all pjproject library, the permission to access the header file installed is "none".(I right click on one of the file in /usr/local/include , then choose properties , then select the permission tab, then the grou access is "None" and others access is "None" also. 

So I'm wondering is it my Ubuntu setting problem? The true setting for the header file in /usr/local/include should be "read only for both 'group' and 'others' access right?

---

### Post by taurus on 2009-03-14
You can look at the permissions of other files in that same directory to see what they are.  Then, change the new one to have the same permissions as the current ones.

```
sudo chmod 644 filename
```

Where did you install the new version of vlc that you built/modified?

---

### Post by wssoh85 on 2009-03-14
The vlc not yet install since during the ./configure step, it would check for those header 1st. So it keep complain that the some the header file not found.

---

