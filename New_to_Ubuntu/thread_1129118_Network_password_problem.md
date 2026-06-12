---
title: "Network password problem"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by rodneysores on 2009-04-18
I have a desktop running Ubuntu and a laptop running Vista.  I've had the network working fine but this morning all of a sudden Vista is asking me for a password to access the Ubuntu machine and the Vista doesn't appear under Places>Network.  I typed in the Vista username and password 'administrator' which allows me to see the shared folders on the Ubuntu machine, but when I try to open one, it asks for another username and password.  This one I can't get past.  I've made no changes since it worked so any help would be great.

---

### Post by coldReactive on 2009-04-18
Have you tried using the username and password of the ubuntu machine?

---

### Post by rodneysores on 2009-04-23
Yes, I have tried that.  It just says "Ubuntu_machine is not accessible, you may not have permission etc."  I have however regained access to the vista machine from ubuntu - I clicked on Network Manager icon, clicked on Auto etho, it did some thinking and voila.

---

### Post by doas777 on 2009-04-23
in your /etc/samba/smb.conf
add the line:
```
client NTLMv2 auth = yes
```

Vista uses ntlmv2 passwords exclusively, so unless you allow the mechanism in samba, the two can never talk, unless you up samba to v2, or reduce the vista security to ntlm or lm.

good luck

(Note: I just found and corrected a typo in my code line. it should read "NTLMv2", not "NTMLv2"). sorry about that

---

### Post by rodneysores on 2009-04-24
I've tried to add the line but cannot save - "Could not save file, you do not have permissions necessary etc"  Any thoughts?

---

### Post by doas777 on 2009-04-24
> **rodneysores said:**
> I've tried to add the line but cannot save - "Could not save file, you do not have permissions necessary etc"  Any thoughts?

ahh, you prolly forgot sudo/gksu. open a terminal (or alt+F2)and enter this:
```

gksu gedit /etc/samba/smb.conf

```

if you get an error, or the file is empty, then you don;t have samba installed you can add it with:
```

sudo apt-get install samba

```

---

### Post by rodneysores on 2009-04-25
Ok, so I typed that line, was prompted for a password and now I am able to save.  I added "client NTLMv2 auth = yes" and saved.  There doesn't seem to be any change.  Just to be clear, I am able to view the folders that are shared on Ubuntu from the vista machine but I can't open them without entering a username and password that I don't know.  Thanks.

---

### Post by doas777 on 2009-04-25
> **rodneysores said:**
> Ok, so I typed that line, was prompted for a password and now I am able to save.  I added "client NTLMv2 auth = yes" and saved.  There doesn't seem to be any change.  Just to be clear, I am able to view the folders that are shared on Ubuntu from the vista machine but I can't open them without entering a username and password that I don't know.  Thanks.

when you opened the file, was it empty, or already full of text?
if it was empty, install samba.

also I forgot to mention that you need to restart samba or reboot before the changes will be effective. sorry 'bout that.
you can restart samba with:
```

sudo /etc/init.d/samba restart

```

have fun

---

### Post by rodneysores on 2009-04-26
When I opened it, it was full of text.  I added the line and rebooted and no change.  Are there any permission settings that will allow unrestricted access from within my secure connection?

---

### Post by doas777 on 2009-04-26
well you can reduce the security in vista. the settings are in secpol.msc if you have vista business/enterprise/ultimate. if you are using home premium, then it requires registery editing.

---

### Post by rodneysores on 2009-04-28
I can access the vista machine with no troubles, it's wide open for sharing, no passwords required - the problem is fully accessing the ubuntu machine - it won't let me in, it just lets me look in the window so to speak.

---

### Post by doas777 on 2009-04-28
> **rodneysores said:**
> I can access the vista machine with no troubles, it's wide open for sharing, no passwords required - the problem is fully accessing the ubuntu machine - it won't let me in, it just lets me look in the window so to speak.

ok, you probably need to add a samba user. on the ubuntu box, and enter
```

sudo  smbpasswd -a <UsernameOnVistabox>

```

now try to connect

---

### Post by rodneysores on 2009-04-29
Thanks for your help so far.  We've taken a step back now.  No change to original problem and now; vista sees ubuntu but can't open (as before), ubuntu can no longer see vista.  Samba is running.

---

