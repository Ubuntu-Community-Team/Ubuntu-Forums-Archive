---
title: "Internal microphone doesn't work with web browsers/flash. Flash changes mixer setting"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by NoPoChris on 2011-07-08
Ububtu 11.04 on Asus EEE PC1001PXB

I had the same problem as in [this thread]("http://ubuntuforums.org/showthread.php?p=11027758#post11027758") and was able to partially solve it based on what the OP figured out. 

Basically, when using the webcam no sound is captured by the internal microphone. By changing the Pulse Audio input settings to 75% front left and 10% front right I was able to get the microphone to work with Skype by disabling the "Allow Skype to automatically adjust my mixer levels" option. However, when trying to use a video chat service that uses Flash in my web browser (Google Talk, Google+ Hangout) the left and right channels are automatically reset and locked together. Is there a way to block Flash from changing those settings or can I somehow lock the Pulse mixer so the levels can't be changed?

---

### Post by NoPoChris on 2011-07-10
Maybe a quick bump will help?

---

