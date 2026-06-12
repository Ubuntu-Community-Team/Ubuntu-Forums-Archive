---
title: "New to ubuntu; rhythmbox is not playing music."
date: 2010-07-02
forum: New to Ubuntu
---

### Post by brooke1011 on 2010-07-02
I'm new, and I cannot get rhythmbox to play music. Whenever I try to play music, this message appears: "Your Gstreamer installation is missing a plugin". Does anyone know how to fix this??

---

### Post by rcayea on 2010-07-02
> **brooke1011 said:**
> I'm new, and I cannot get rhythmbox to play music. Whenever I try to play music, this message appears: "Your Gstreamer installation is missing a plugin". Does anyone know how to fix this??

Copy this into a terminal:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

I got that long terminal command from the medibuntu site which is located here:
[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by brooke1011 on 2010-07-02
Okay I entered it. Now it says, "[sudo] password for brooke" I tried to enter my password but it's not working. Like I said, I'm new. haha.

---

### Post by rcayea on 2010-07-02
Do you possibly have the caps-lock on? You want the password you entered during setup.

---

### Post by brooke1011 on 2010-07-02
Wait so the password I used to log on to Ubuntu?

---

### Post by rcayea on 2010-07-02
yes. that is your "sudo" password, meaning your Super User DO password

---

### Post by brooke1011 on 2010-07-02
never mind! i got the password and a whole bunch of stuff happened on the terminal. so is it fixed now or do i have to do more?

---

### Post by rcayea on 2010-07-02
The terminal probably had a bunch of lines pass before your eyes, right?

That is the computer doing the work. In linux you get to see what is happening. Some of us like it this way. 

So now, to play it safe, type into the terminal:
sudo apt-get update

Once you do this you should be able to go to Rhythmbox and play songs.

---

### Post by limestone on 2010-07-02
just install ffmpeg gstreamer plugin, search in synaptic for mp3

---

### Post by warfacegod on 2010-07-02
> **rcayea said:**
> Copy this into a terminal:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

I got that long terminal command from the medibuntu site which is located here:
[http://medibuntu.org/](http://medibuntu.org/)

This seems like allot for what should be fairly simple:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by lkjoel on 2010-07-02
> **rcayea said:**
> The terminal probably had a bunch of lines pass before your eyes, right?

That is the computer doing the work. In linux you get to see what is happening. Some of us like it this way. 

So now, to play it safe, type into the terminal:
sudo apt-get update
**sudo apt-get upgrade**

Once you do this you should be able to go to Rhythmbox and play songs.
rcayea, did you mean that?

---

### Post by rcayea on 2010-07-07
Yes, I did. Thank you for correcting my error.

Randy

---

### Post by lkjoel on 2010-07-07
Or
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Depending on what you want;)

---

### Post by garethfoxwilliams on 2010-07-08
"Ubuntu Restricted Extras" is/are available through the Ubuntu Software Centre.

The package contains all the "non-free" stuff ie:
True Type fonts
Java
Flash
Codecs
etc. etc.

By "non-free", we mean 'free as in beer' but not 'free as in speech' .
Ubuntu cannot include these in the downloadable distros as they will infringe some countries' local laws, but as you will see it's easy to get them post install.

---

### Post by Paqman on 2010-07-08
> **garethfoxwilliams said:**
> "Ubuntu Restricted Extras" is/are available through the Ubuntu Software Centre.


+1 

Medibuntu is nice to have, but not actually necessary to get mp3 playback in Rhythmbox. Installing the restricted extras package will kill off all your codec and multimedia woes in one simple step.

---

