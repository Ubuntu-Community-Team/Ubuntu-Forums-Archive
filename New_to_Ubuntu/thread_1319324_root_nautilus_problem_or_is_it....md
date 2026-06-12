---
title: "root nautilus problem or is it...?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by dan1973 on 2009-11-08
when I gksudo nautilus i get the following message in the terminal:

[PHP]dan@dan-laptop:~$ gksudo nautilus
** Message: Initializing gksu extension...
Initializing nautilus-gdu extension

** (nautilus:2877): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2877): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2877): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2877): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
dan@dan-laptop:~$[/PHP] 


Nautilus does however start up with root acess. Don't like to have the wierd messages. Could someone please explain what it means and if / how I should go about handling it.

Many thanks in advance.

---

### Post by jbrown96 on 2009-11-08
I'm guessing that "marshallers" are plugins. They extend the functionality of Nautilus. You don't have the plugins installed, and it's politely telling you so. Generally you never need to worry about warnings on the command line. Those are mostly for developers; errors are what matter. 
I think the first three are related to samba (network file sharing). They all come from the third warning that samba isn't configured. 


Do the same warnings show up when you run nautilus as a normal user?

Running nautilus as root is almost always a bad idea. You can really mess up your system if you do something wrong. Try to learn the terminal commands.

---

### Post by dan1973 on 2009-11-08
this is the message i get when running just the nautilus command:-

```
dan@dan-laptop:~$ nautilus

(nautilus:3062): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
dan@dan-laptop:~$ 
```

Have been learning to utilize shell and the terminal, hoever have always been a better 'clicker' than a 'typer' - also have a very visually oriented brain ( also some dislexia ) and so graphical manipulation seems to suit me best if it is possible.

I only resort to command when it is either easier for me or much quicker.
 
I think it's the understanding which is important, and i do agree that if one is just pointing and clicking endlessly without some sort of understanding of what is going on 'underneath', a lot can be missed or executed in error.

But, back to the problem at hand - is there one?

---

### Post by Flywaver on 2009-11-09
I have the exact same messages when I run nautilus in root or in regular mode! I don't like seeing warning msg either! :(

---

### Post by jbrown96 on 2009-11-09
warnings don't matter. They are for developers. If you really don't like the warnings, you can redirect them to /dev/null ```
sudo nautilus 2&> /dev/null
``` That just makes it so you can't see them.

---

