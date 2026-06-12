---
title: "How do I enable Automatic Keyring Login? 9.10"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by TheParadox on 2010-02-09
Im on 9.10 Karmic Kola. How do I set it so I dont have to login to the keyring?

---

### Post by patchwork on 2010-02-09
Is this after resuming from hibernate or suspend?  

If so, I think I know this.  Best to wait for confirmation from someone more experienced, however.

Open the gconf-editor
```
gconf-editor
```

click on:

apps > gnome-power-manager > lock

and uncheck gnome-keyring hibernate and gnome-keyring suspend

---

### Post by TheParadox on 2010-02-09
Well this to work when starting from powered off as well or post-power failure. This is on a local and wan development server with a gui. (Hence why its not on Ethernet its not as important)

---

### Post by patchwork on 2010-02-09
That I'm not sure.  I did some googling, but the responses I found I'm not really comfortable trying on my own computer, let alone telling you to try it on yours....(involves deleting some files...)

---

### Post by noelvh on 2010-02-09
I am not going to say this is the right way or the wrong way but this is the way I have done this but it is to remove the password for the key ring. I then create a balnk password for the key ring.

Open a terminal drop this in there and this will do it.
```
rm ~/.gnome2/keyrings/*.keyring
```

I have to say or all things in Ubuntu I hate the key ring, and I feel I should be asked if I want to use it. I have never used it nor will I use it. I have a password on my laptop why do I need one for my key ring so I can do my wifi. Now I am sure there are good reasons to use it but I am sure most do not need it or want it or know they don't have to have it.

If I am wrong let me know.

Noel

---

### Post by TheParadox on 2010-02-09
> **noelvh said:**
> I am not going to say this is the right way or the wrong way but this is the way I have done this but it is to remove the password for the key ring. I then create a balnk password for the key ring.

Open a terminal drop this in there and this will do it.
```
rm ~/.gnome2/keyrings/*.keyring
```I have to say or all things in Ubuntu I hate the key ring, and I feel I should be asked if I want to use it. I have never used it nor will I use it. I have a password on my laptop why do I need one for my key ring so I can do my wifi. Now I am sure there are good reasons to use it but I am sure most do not need it or want it or know they don't have to have it.

If I am wrong let me know.

Noel
Thank you! I will try this. Yeah keychain is useless to me. Have a strong enough password at login whats the point of a keychain? As long as you lock your computer when you dont want people accessing it your fine. I will report back after I try this. Thanks again.

---

