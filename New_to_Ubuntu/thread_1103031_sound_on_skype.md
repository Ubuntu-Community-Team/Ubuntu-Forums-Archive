---
title: "sound on skype"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by DarinB on 2009-03-22
i installed skype for deb and it comes up audio problems

---

### Post by llamabr on 2009-03-22
This is a faq.

[http://www.google.com/search?q=cache:RsGSkVn3HUYJ:ubuntuforums.org/archive/index.php/t-53792.html+ubuntu+skype+sound&cd=8&hl=en&ct=clnk&gl=us&client=firefox-a](http://www.google.com/search?q=cache:RsGSkVn3HUYJ:ubuntuforums.org/archive/index.php/t-53792.html+ubuntu+skype+sound&cd=8&hl=en&ct=clnk&gl=us&client=firefox-a)

I find that I have to mess with the settings to get it to work.  I also recall something about installing or removing pulseaudio.

Have you tried asking google?

---

### Post by Dedoimedo on 2009-03-22
Elaborate?
Dedoimedo

---

### Post by Sef on 2009-03-22
1) Did you download skype for Ubuntu?  If not, then remove skype, and download [that one]("http://www.skype.com/download/skype/linux/choose/").

2) Which version of Ubuntu do you have?

---

### Post by DarinB on 2009-03-22
i downloaded the one that says deb and i don't have it in synaptic

---

### Post by DarinB on 2009-03-22
the version is 2.0.0.72

---

### Post by DarinB on 2009-03-22
still no sound i removed the skype and added it from the medibuntu repo it added a few dependencies but i still get the audio error on phone test.

---

### Post by leonardo_neo on 2009-03-22
Hi,

I had the similar problem. Well you need not to uninstall pulse audio. Try this first.

Run skype, and login. Then click on the skype icon bottom left. Select 'Options'. Then select "Sound devices"

In 'sound out' and 'ringing' section, select 'pulse'.

In 'sound in' option select Intel ICH6 (hw:ICH6,O)

Make a test call. If that doesn't work, then from 'sound in' option, test other options one by one, and make test call.

Hope this helps. :)

---

### Post by DarinB on 2009-03-22
i dont have ich6 i have ich2 but it worked with sound i am having problems with the skype phone it does not see it

---

### Post by DarinB on 2009-03-22
i got the USB phone to work by choosing sound options in skype i changed sound in and sound out to usb phone plughw:,default0 i left ring to pulse and i will see what happens when i get a call

---

### Post by chuuk on 2009-03-22
Kill pulseaudio using gnome-system-monitor or the command line...no need to uninstall it.

---

