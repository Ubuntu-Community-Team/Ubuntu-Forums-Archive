---
title: "dvd play"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by kevin walsh on 2010-03-20
I'm trying get playback of DVD's on my computer. I've installed The totem programs as well as all the gstreamer plugins I can find. Still no luck playing DVD's. When I try totem tells me install plugins??? I thought I had... What am I doing wrong?

---

### Post by lisati on 2010-03-20
Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by derekeverett on 2010-03-20
You could also install VLC. Personally I prefer it is a media player.

---

### Post by 2hot6ft2 on 2010-03-20
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```
type in your password when prompted and hit Enter it wont be displayed.

Forgot you'll have to accept the agreement for java which I'm sure you'll be wanting too.

---

### Post by QIII on 2010-03-20
You need something lib libdvdcss2 to decode the DVDs.

Take a look at 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Execute the following in the terminal

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 
```

Then, further down the page, you will see to run this in the terminal:

```
sudo apt-get install libdvdcss2
```

---

### Post by kcohen1017 on 2010-03-21
This is the article that saved the day for me - 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I followed these step by step, and viola! my system now plays DVDs perfectly.

---

### Post by Ozymandias_117 on 2010-03-21
When your problem is fixed, please click on "Thread Tools" at the top of the thread and select "Mark as Solved"

---

