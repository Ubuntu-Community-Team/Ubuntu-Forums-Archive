---
title: "[SOLVED] How to Uninstall a program"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by vagelism on 2008-12-29
Hello to all.

I downloaded KOMODO 5 IDE I thought is free but now I see there is only a 21 day trial. I am new one to Linux so please anyone can help me to uninstall it.

THANK YOU.

---

### Post by taurus on 2008-12-29
How did you install it?

---

### Post by Sealbhach on 2008-12-29
Looking at his other recent post, he got a tar.gz from here:

[http://www.activestate.com/Products/komodo_ide/komodo_edit.mhtml](http://www.activestate.com/Products/komodo_ide/komodo_edit.mhtml)


.

---

### Post by moonoo on 2008-12-29
You could try locating it within Synaptic (apt manager).

To start Synaptic go to:
System > Administration > Synaptic Package Manager.

By default, you will have three panes:
Two on left and one right.

Select 'Status' fro the bottom left then select 'Installed (Local or obsolete)' from the top left panee.

If the package is listed there, untick and select apply from the top menu bar.

There is alway an easier way using the command line if you're happier with that..:D

Hope that helps

---

### Post by Bölvaður on 2008-12-29
oh god... please use Synaptic for installing programs or .deb files rather than going to random webpages like if you would be on windows.

1. System &#8594; Administrator &#8594; Synstapic Package Manager
2. Applications &#8594; Add/Remove
3. [www.getdeb.net](www.getdeb.net)

---

### Post by thomasr on 2008-12-29
> **Bölvaður said:**
> oh god... please use Synaptic for installing programs or .deb files rather than going to random webpages like if you would be on windows.

1. System &#8594; Administrator &#8594; Synstapic Package Manager
2. Applications &#8594; Add/Remove
3. [www.getdeb.net](www.getdeb.net)

 But there are programs not available as Debs - for example, vmware server.

---

### Post by taurus on 2008-12-29
Here's the section of uninstall for Unix/Linux.

> 
**Uninstalling Komodo on Linux**

To uninstall Komodo on Linux:

   1. Delete the directory that Komodo created during installation.
   2. If you wish to delete your Komodo preferences, delete the ~/.komodo directory. If you do not delete this directory, subsequent installations of Komodo will use the same preferences.


---

### Post by handydan918 on 2008-12-29
> **vagelism said:**
> Hello to all.

I downloaded KOMODO 5 IDE I thought is free but now I see there is only a 21 day trial. I am new one to Linux so please anyone can help me to uninstall it.

THANK YOU.

Just for giggles and grins, I installed this, because I have never in ten years seen a "trialware" program for Linux. I don't see one now, as far as I can tell. 

Be that as it may...
never mind all the well intentioned advice to use synaptic or any other package manager to remove this. It won't work. 
Locate the directory you installed to and right click it. This should give you the option to delete it. On my system that is ```
/home/daniel/Komodo-Edit-5.0.3-2767-linux-libcpp6-x86
```If you would rather do it from a terminal, just enter the path, like above, but corrected for the location on your system, and do ```
rm -rf /home/<username>/Komodo-Edit-5.0.3-2767-linux-libcpp6-x86
``` 


Yeah, it's that simple. It doesn't scatter irretrievable crap hither and yon like that OTHER operating system...

HTH!!

---

### Post by vagelism on 2008-12-29
Hello.

I runed an install script something like a install.sh
after this all was automatic.
I have a new directory in my home dir called komodo (something..)
and a icon on my desktop that i can run the ptogram
thats all.

---

### Post by Sealbhach on 2008-12-29
Yeah, with some software you just extract it and run it all out of one folder in your /home directory, so it just a matter of deleting the folder and any .folder that it made as well.


.

---

### Post by vagelism on 2008-12-29
I do not see anything there
please give me the  command line

---

### Post by vagelism on 2008-12-29
> **handydan918 said:**
> Just for giggles and grins, I installed this, because I have never in ten years seen a "trialware" program for Linux. I don't see one now, as far as I can tell. 

Be that as it may...
never mind all the well intentioned advice to use synaptic or any other package manager to remove this. It won't work. 
Locate the directory you installed to and right click it. This should give you the option to delete it. On my system that is ```
/home/daniel/Komodo-Edit-5.0.3-2767-linux-libcpp6-x86
```If you would rather do it from a terminal, just enter the path, like above, but corrected for the location on your system, and do ```
rm -rf /home/<username>/Komodo-Edit-5.0.3-2767-linux-libcpp6-x86
``` 


Yeah, it's that simple. It doesn't scatter irretrievable crap hither and yon like that OTHER operating system...

HTH!!

thanks seems that it worked...
I do not have the directory anymore and of course nothing inside.
Is there a case to have any broken packages?
Thank you.

---

### Post by Sealbhach on 2008-12-29
You may also have a .komodo folder in your /home directory. Go into Nautilus and press Ctrl+H to show hidden files. See if it's there and if it is, delete it.


.

---

### Post by handydan918 on 2008-12-29
> **vagelism said:**
> thanks seems that it worked...
I do not have the directory anymore and of course nothing inside.
Is there a case to have any broken packages?
Thank you.
Not in my wildest imagination can I figure a way this would cause b0rken packages.

---

### Post by saidbakr on 2010-08-06
Hi,
I would like to understand the command
rm -rfwhich I used it to remove Komodo edit 6 Beta.

---

