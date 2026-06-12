---
title: "Should have waited to upgrade to 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Kangaroo_Style on 2010-05-02
Computer was running fine under 9.10. Now I have a problem with PulseAudio that says, "Waiting for sound system to respond"

And to top it off, I have some ICE error when I try to login. 

Not to mention my Rhythmbox still isn't working since the upgrade.

10.04 has been a bigger pain than it's worth...

---

### Post by sadaruwan12 on 2010-05-02
> **Kangaroo_Style said:**
> Computer was running fine under 9.10. Now I have a problem with PulseAudio that says, "Waiting for sound system to respond"

And to top it off, I have some ICE error when I try to login. 

Not to mention my Rhythmbox still isn't working since the upgrade.

10.04 has been a bigger pain than it's worth...

Did you do a clean install or a upgrade through the upgrade manager ?

---

### Post by Kangaroo_Style on 2010-05-02
> **sadaruwan12 said:**
> Did you do a clean install or a upgrade through the upgrade manager ?


Went through the upgrade manager. 

Luckily for me I still have sound in Skype, and I can voice/video chat. Which is essential for me right now. 

1. I cannot adjust volume, due not being able to access sound menu through > preferences > sound
2. I cannot use Rhythmbox (I just switched to Banshee and that works great, but it's just a work around instead of a solution) [Solved] - (sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12) Fixed the problem.
3. Now I get some ICE error, that I've never had before. 

I've been going through old threads where people have had the same problem and tried deleting the .pulse folder, and I tried uninstalling and reinstalling Pulseaudio to no avail.

---

### Post by madjr on 2010-05-02
i always try the live-cd or installing to a new partition (keeping both versions)

never had a problem when i do this or just use the older, till an update fixes the problem

you should probably reinstall 10.04 from cd, seems like a bad install. remember to backup

---

### Post by Kangaroo_Style on 2010-05-02
> **madjr said:**
> i always try the live-cd and another partition

you should probably reinstall 10.04 from cd, remember to backup


Yeah, I think that's the next step. Luckily, I was able to configure Skype to still work. However I don't have the means to get an external hard drive at the moment to back everything up.  But this just goes to show that it's an investment I need to make soon.

---

### Post by sadaruwan12 on 2010-05-02
> **Kangaroo_Style said:**
> Went through the upgrade manager. 

Luckily for me I still have sound in Skype, and I can voice/video chat. Which is essential for me right now. 

1. I cannot adjust volume, due not being able to access sound menu through > preferences > sound
2. I cannot use Rhythmbox (I just switched to Banshee and that works great, but it's just a work around instead of a solution) [Solved] - (sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12) Fixed the problem.
3. Now I get some ICE error, that I've never had before. 

I've been going through old threads where people have had the same problem and tried deleting the .pulse folder, and I tried uninstalling and reinstalling Pulseaudio to no avail.


Could you tell what is your ICE error and I used 9.10 earlier what I did I just cleaned installed every thing. It advised to do a clean installation when you're migrating to a newer OS.

Try to do a clean installation cos it also create a new hardware profile and might solve your issue.

---

### Post by lidex on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=949750]("http://ubuntuforums.org/showthread.php?t=949750")

---

