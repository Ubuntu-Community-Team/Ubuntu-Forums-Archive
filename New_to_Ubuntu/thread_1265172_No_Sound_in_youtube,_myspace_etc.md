---
title: "No Sound in youtube, myspace etc"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-09-13
I get video fine just no sound.  I am using Konqueror.

---

### Post by isparkes on 2009-09-13
I had something like this because I was using the wrong version of the flash plugin. This was using firefox, though.

Remove all other flash (gnash) versions and install 

```
flashplugin-nonfree 
```

Just an idea...

---

### Post by Dobbie03 on 2009-09-13
I have no idea how to update it...

---

### Post by isparkes on 2009-09-13
sorry, after posting  I realised that the message wasn't that helpful, so I edited it. It's still early morning here, so not at 100% yet... :)

In a terminal 

```
sudo apt-get install flashplugin-nonfree
```

Repeat, this was for firefox, but it could have the same root cause, so worth a try.

---

### Post by Dobbie03 on 2009-09-13
I know that feeling all too well. Supposedly my version is the latest :(  

edit: I am updating to the latest Firefox hopefully this will fix the prob.

---

### Post by Dobbie03 on 2009-09-13
I updated Firefox to 3.5.3 and no luck.  No sound in either Firefox or Konqueror.  Anyone have any ideas?

---

### Post by redbob on 2009-09-13
Open the following folder
> /usr/lib/firefox/plugins
Tell us what you've got at there.

---

### Post by sanguinoso on 2009-09-14
Also do you have multiple sound cards? I had a problem with flash after I set up PulseAudio with the two sound cards.

---

### Post by Dobbie03 on 2009-09-14
> **redbob said:**
> Open the following folder

Tell us what you've got at there.

I have *flashplugin-alternative.so*


@ sanguinoso:  No I have one sound card.

---

### Post by Dobbie03 on 2009-09-14
Can anyone help me?

---

### Post by dzon65 on 2009-09-16
Make sure you have only one flashplugin.Two or more can conflict.Go to synaptics ,type flash and look if there's more than one installed.

---

### Post by wgargan on 2009-10-06
alsamixer -Dhw

---

