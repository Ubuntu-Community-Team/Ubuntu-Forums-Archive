---
title: "Help me plz!"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by naveedmanzoor21 on 2010-03-10
Hello everyone please help me with this

i have an Ubuntu 9.04-Jaunty on my system.... The problem is, when i open Computer from Places > Computer in my system the File Browser automatically closes all the file browsers opened on my desktop, it also disables right-click on Desktop and hides all files & icons visible on Desktop. 

So, any one can help me with this... I cant even open my clients  Fedora system root directory ('/') while connecting them through SSH ...

Please tell me whats the problem is..!

---

### Post by Elaztic on 2010-03-10
Try to run nautilus (the file browser) from the terminal and see if it gives you any error messages.
Perhaps you can even set a verbose flag (-v) for more info but you would have to play around with the terminal to see what options you have.
Sorry I cannot help more right now but I am at work where we use Windoze :(

---

### Post by naveedmanzoor21 on 2010-03-10
> **Elaztic said:**
> Try to run nautilus (the file browser) from the terminal and see if it gives you any error messages.
Perhaps you can even set a verbose flag (-v) for more info but you would have to play around with the terminal to see what options you have.
Sorry I cannot help more right now but I am at work where we use Windoze :(

Thanks for replying :)
on running nautilus i'm getting following error
dtel@dtel-desktop:~$ nautilus

(nautilus:17995): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

---

### Post by naveedmanzoor21 on 2010-03-10
i will try other options ....

---

### Post by naveedmanzoor21 on 2010-03-10
ON RUNNING NAUTILUS AFTER BECOMING SU, IM GETTING FOLLOWING ERROR'S

root@dtel-desktop:/usr/src# nautilus

(nautilus:28202): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


(nautilus:28202): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf warning: failure listing pairs in `/apps/nautilus/preferences': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/desktop/gnome/file_views': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/desktop/gnome/background': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/desktop/gnome/lockdown': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/apps/nautilus/desktop': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/apps/nautilus/icon_view': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)GConf warning: failure listing pairs in `/apps/nautilus/desktop-metadata': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(nautilus:28202): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:28202): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.

(nautilus:28202): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:28202): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.

(nautilus:28202): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

---

### Post by undecim on 2010-03-10
I think the error you are getting is unrelated to the crash, because it's reported here and isn't causing a crash :[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

When running nautilus from the terminal did you try to make it crash? If you've already done that and got no error when it crashed, the command
```
strace nautilus 2> strace.nautilus.txt
```
will write VERY detailed debugging info to the file strace.nautilus.txt, which you can post here as an attachment.

---

### Post by naveedmanzoor21 on 2010-03-11
> **undecim said:**
> I think the error you are getting is unrelated to the crash, because it's reported here and isn't causing a crash :[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

When running nautilus from the terminal did you try to make it crash? If you've already done that and got no error when it crashed, the command
```
strace nautilus 2> strace.nautilus.txt
```
will write VERY detailed debugging info to the file strace.nautilus.txt, which you can post here as an attachment.

here it is what i got
download it from the following link: [http://www.2shared.com/file/12021628/f0d331c5/stracenautilus.html]("http://www.2shared.com/file/12021628/f0d331c5/stracenautilus.html")

---

### Post by undecim on 2010-03-11
> **naveedmanzoor21 said:**
> here it is what i got
download it from the following link: [http://www.2shared.com/file/12021628/f0d331c5/stracenautilus.html]("http://www.2shared.com/file/12021628/f0d331c5/stracenautilus.html")

I can't download the file from the link.

can you please post it as an attachment here?

---

### Post by naveedmanzoor21 on 2010-03-12
> **undecim said:**
> I can't download the file from the link.

can you please post it as an attachment here?

ok i will post it here

---

### Post by naveedmanzoor21 on 2010-03-12
> **naveedmanzoor21 said:**
> ok i will post it here

i think u can download this

---

