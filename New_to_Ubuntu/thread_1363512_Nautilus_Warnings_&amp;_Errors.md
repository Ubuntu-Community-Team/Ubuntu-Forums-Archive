---
title: "Nautilus Warnings &amp; Errors"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-24
**I'm posting this again in hopes someone has an idea what this means and a possible fix, or maybe suggest another forum that deals with this type of problem.  Being new to Ubuntu I'm completely stumped**. :confused:

jnmjr@My-Desktop:~$ sudo nautilus
[sudo] password for jnmjr: 

(nautilus:3506): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

** (nautilus:3506): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3506): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3506): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** Message: Initializing gksu extension...
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> l2065
--> inode/directory
--> root

(nautilus:3506): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:3506): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 5 elements at quit time
Shutting down nautilus-open-terminal extension
Shutting down nautilus-gdu extension
jnmjr@My-Desktop:~$

**If I try:** 

jnmjr@My-Desktop:~$ gksudo nautilus
(nautilus:3670): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

** (nautilus:3670): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3670): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3670): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** Message: Initializing gksu extension...
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> l2065
--> inode/directory
--> root
Shutting down nautilus-open-terminal extension
Shutting down nautilus-gdu extension

(nautilus:3670): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:3670): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
jnmjr@My-Desktop:~$

---

### Post by cariboo on 2009-12-24
When you run nautilus as a normal user, does it work properly? the only thing I see is that a couple of extensions aren't being loaded properly:

[list]
[*] nautilus-open-terminal extension
[*] nautilus-gdu extension
[/list]

I would suggest removing the extensions, and see if that solves the problem.

---

### Post by Zoot7 on 2009-12-24
Try this - open up the Synaptic Package Manager and run a search for Nautilus.
Mark it for complete removal and then re-install it.

---

### Post by jnmjr on 2009-12-26
Now I really did it, I lost my gnome desktop. When I log in I get a small terminal;
 
jnmjr@My-Desktop: ~$
 
Ok so I re-installed nautilus went OK.... next tried:
 
sudo apt-get install gnome
 
 
The following packages have not met dependencies:
 
Gnome depends:gnome-desktop-environment=(1:2.22.2ubuntu) But is not going to be installed
Depends:gnome-vfs-obexftp but it is not installable
E:Broken packages
 
jnmjr@My-Desktop:~$

---

### Post by jnmjr on 2009-12-26
How can I get my desktop back, I really don,t want to re- install the whole Ubuntu 9.10. THX

---

### Post by oldos2er on 2009-12-26
You could try ```
sudo apt-get install -f && sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by jnmjr on 2009-12-26
Is this one command or is it three different commands.THX

---

### Post by CharlesA on 2009-12-26
One command the  && tells it to only run those commands if the previous one was successful.

---

### Post by jnmjr on 2009-12-26
You guys are great, I got it back, thanks so much.

---

### Post by jnmjr on 2009-12-26
Tried  Sudo nautilus in terminal, this is what I get :

jnmjr@My-Desktop:~$ sudo nautilus

(nautilus:2215): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2215): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2215): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2215): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2215): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

(nautilus:2215): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Shutting down nautilus-gdu extension
jnmjr@My-Desktop:~$ 

Nautilus is now working so I suppose that this stuff is just a bug?????:confused:

---

### Post by oldos2er on 2009-12-26
You should use **gksu** when calling graphical programs like Nautilus, instead of sudo. Here's why: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

I get similar warnings when running gksu nautilus, but it runs fine. I just ignore them.

---

### Post by jnmjr on 2009-12-26
Thanks for the heads-up, true I get the same warnings using gksudo but it works. If I may...without starting a new thread.... Can you explain what this means and how do I go about adding and enabling it so that it doesn't come up anymore!!

MAKE SURE ALL REQUIRED REPOSITORIES ARE ADDED AND ENABLED IN THE PREFERENCES.

Thank you very, very much for your help.

---

### Post by oldos2er on 2009-12-26
What app are you using when this message comes up?

You can check repositories via the menus System, Administration, Software Sources.

---

### Post by jnmjr on 2009-12-27
Thanks for your answer, this came up a while back at the very beginning when I was installing some packages thru synaptic so some software would run, I consequently decided to forget the whole thing, didn't need it any ways, I wrote down the message but didn't write the packages' names. Don't even remember what I ate for breakfast LOL. Just used this opportunity to ask. Thanks again.

---

### Post by Zoot7 on 2009-12-27
> **oldos2er said:**
> I get similar warnings when running gksu nautilus, but it runs fine. I just ignore them.
Ditto.

---

### Post by afrodeity on 2010-02-07
I'm having similar trouble with Nautilus. See here [http://ubuntuforums.org/showthread.php?t=1399819](http://ubuntuforums.org/showthread.php?t=1399819)

---

