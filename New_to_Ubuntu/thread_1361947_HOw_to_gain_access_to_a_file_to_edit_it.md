---
title: "HOw to gain access to a file to edit it?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-22
Ubunteros,

I installed this program called Polipo following the instructions found at:


[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

Step Two: Install Polipo for Web Browsing

Once you've installed Polipo (either from package or from source), you will need to configure Polipo to use Tor. Grab our Polipo configuration for Tor and put it in place of your current polipo config file (e.g. /etc/polipo/config or ~/.polipo). You'll need to restart Polipo for the changes to take effect. For example:
/etc/init.d/polipo restart

I went to terminal and entered gedit then navigated to the file in question but it does not allow me to save it. What can I do?

Thank you!!!!

---

### Post by dyous87 on 2009-12-22
> **suomalainen said:**
> Ubunteros,

I installed this program called Polipo following the instructions found at:


[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

Step Two: Install Polipo for Web Browsing

Once you've installed Polipo (either from package or from source), you will need to configure Polipo to use Tor. Grab our Polipo configuration for Tor and put it in place of your current polipo config file (e.g. /etc/polipo/config or ~/.polipo). You'll need to restart Polipo for the changes to take effect. For example:
/etc/init.d/polipo restart

I went to terminal and entered gedit then navigated to the file in question but it does not allow me to save it. What can I do?

Thank you!!!!

You need to run this file as root to save it.

```
gksudo gedit /etc/polipo/config
```This will ask for your password. You will then be able to edit the file with gedit and save it.

Just for future reference, anything not in your home directory '/home/USER' cannot be written to unless you have super user privileges. This is a security feature built into all Linux/ UNIX based operating systems. 

Cheers,
David

---

### Post by audiomick on 2009-12-22
> **suomalainen said:**
> 
I went to terminal and entered gedit then navigated to the file in question but it does not allow me to save it. What can I do?

Thank you!!!!

/etc belongs to root. You have to start gedit with root privileges.

Do
```
gksu gedit /path/to/file
```

you will be asked for your password. Enter your login password. You will not see what you are typing.

Be careful with this. Gaining root privileges puts you in a position to break your system if you do something wrong.:)

---

### Post by suomalainen on 2009-12-22
Is there any problem if I edited the file using sudo gedit and then navigating to the file in question?

That's what I did.

---

### Post by dyous87 on 2009-12-22
No that would work to. Just keep in mind for the future, when ever you're trying to run a gtk app (GUI) with root priveledges, you should use 'gksudo' instead of just sudo. 

'sudo' should be used for terminal based apps or commands.

Regards,
David

---

### Post by audiomick on 2009-12-22
Hi.
Probably not, I did that for a while, **_but_**

Gedit is a graphical programe, and sudo is for non graphical stuff. gksu is for graphical stuff.

There is an explanation here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

While you are there, have a look around. There is a lot of really useful stuff there.

---

### Post by dyous87 on 2009-12-22
audiomick I just noticed that you use 'gksu' instead of 'gksudo'. Up until now I didn't know that also works. Do you know if there is any difference between the two or are they just aliases to the same program?

David

---

### Post by suomalainen on 2009-12-22
David & Michael,

Thanks for responding back as fast as you did! And especially for providing me with the suggested advice as to when to and not to use "sudo".

Thank You!!!! and Merry Christmas and Happy New Year 2010!!!!!

Suomalainen,

---

### Post by audiomick on 2009-12-22
Hi.
I just did
```
man gksu
```
and
```
man gksudo
```

and got what appears to be the same page.

It starts like this:
> NAME
       gksu - GTK+ frontend for su and sudo

SYNOPSIS
       gksu

       gksu [-u <user>] [options] <command>

       gksudo [-u <user>] [options] <command>

DESCRIPTION
       This manual page documents briefly gksu and gksudo


so it would appear that it is the same thing.

---

### Post by suomalainen on 2009-12-22
But does gksu and gksudo work the same if your using it in conjunction with the "n" word? I guess I mean is it dependent upon degree of privileges your requesting access to.

---

### Post by dyous87 on 2009-12-22
> **suomalainen said:**
> David & Michael,

Thanks for responding back as fast as you did! And especially for providing me with the suggested advice as to when to and not to use "sudo".

Thank You!!!! and Merry Christmas and Happy New Year 2010!!!!!

Suomalainen,

You are very welcome! Merry Christmas and Happy New Year to you as well :)

---

### Post by dyous87 on 2009-12-22
Michael,

Thanks a lot. It appears they are both aliases to the same program which means they can be used interchangeably. 

suomalainen what do you mean by the "n" word?

David

---

### Post by suomalainen on 2009-12-22
As per the "n" word it is my understanding that if you spell this command out on the forum that it is prohibited and can get you banned for a couple of weeks.........

---

### Post by dyous87 on 2009-12-22
I think I may understand what you mean but I am not 100% sure. Regardless if you can get banned we better not say it :)

---

