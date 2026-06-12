---
title: "Unable to download playing dvd software"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by brian mellett on 2009-01-11
I,m new to Linux, running Ubuntu8-10. Had many problems through ignorance, but ever body very helpful and patient. Do I gather correctly that I cannot play dvd's on Linux?for legal reasons. I have been told to enter a sudo code via a terminal to get the software but then get message "require superuser priviledge" Any one help? brian

---

### Post by arochester on 2009-01-11
Add the Medibuntu repository. This page tells you how. Note that it is a 2 stage operation (1) Add repository (2) Get GPG key via terminal

Make sure you have (a) ubuntu-restricted extras and (b) libdvdcss2

---

### Post by UbuntuNerd on 2009-01-11
I made this guide on how to play any media in ubuntu hope is helpful
[http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem]("http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem")

---

### Post by sdowney717 on 2009-01-11
sudo precedes typed commands and gives super user privileges so the commands can run right and change files.
so from terminal type
 
sudo somecommand enter,
then it will prompt you for your login password
type it in and then the command will run properly.

I like VLC for DVD.

---

### Post by bryncoles on 2009-01-11
some reading:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

this is basically needed for doing admin tasks with your computer, and acts as a security layer!

---

### Post by brian mellett on 2009-01-18
> Sorry for delay in replying due to human bug. Ubuntu Nerd , your guide has given me confidence but not enough to proceed. Your other links have made interesting reading. So will not be watching any videos until I gain more knowledge and confidence in Linux.  Brian Mellett

---

### Post by UbuntuNerd on 2009-01-18
hope my blog is got enough information to keep you around and built up your confidence thanks for taking the time to check it out
ubuntunerd

---

