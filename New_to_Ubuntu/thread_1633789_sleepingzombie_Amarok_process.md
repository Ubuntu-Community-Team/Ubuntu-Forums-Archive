---
title: "sleeping/zombie Amarok process"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-11-29
Y'all Ubuntu Community!

Once in a while I try to start Amarok, and it just wont start.

Then, I look in System > administration > System Monitor > Processes, and it shows that I have either a sleeping or Zombie Amarok process.

When I kill the sleeping or Zombie process, I'm then able to start Amarok...

How do I avoid having a sleeping or Zombie Amarok process???

Have in Zombie worries me. If you've ever seen Night of the Living Dead ([http://video.google.com/videoplay?docid=-2956447426428748010#]("http://video.google.com/videoplay?docid=-2956447426428748010#")) you'd understand why.

Thank you,
Phil Smith
Duluthistan, GA

---

### Post by TeoBigusGeekus on 2010-11-29
Launch it from terminal and post any error messages.

---

### Post by Old Jimma on 2010-11-29
It says, "Amarok aleardy running!"

---

### Post by Jetso on 2010-11-29
What about ```
sudo killall amarok & sudo killall <whatever the zombie amarok process is exactly called.> && amarok
```
Just replace <> with what it says. This might provide the output TBG is looking for. 

P.S. I saw the night of the living dead joke. I laughed pretty hard.

---

### Post by TeoBigusGeekus on 2010-11-29
Have you by mistake added it to your startup apps, you know, by saving current session or something?

---

### Post by mc4man on 2010-11-29
It's likely amarok (amarok2 ..?) is not shutting down cleanly. There was an issue early in lucid where this was caused by a failure to complete parsing the music collection or folder(s) containing.

You could try closing out amarok (from sys monitor if need be), installing this package, then try a couple of open and close cycles to see if amarok completely quits.

```
sudo apt-get install mysql-server-core-5.1
```

I believe that's all you need vs installing mysql-server-5.1 itself

orig. bug report
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

---

### Post by Old Jimma on 2010-11-29
Hi Mc4man:

Your solution seemed to work....

However, I had trouble installing [COLOR="Red"]mysql-server-core-5.1[/COLOR] for some reason.

It got stuck and I had to reboot. Then tried to install using synaptic. Synaptic provided code to correct the hung install, then I installed [COLOR="Red"]mysql-server-core-5.1[/COLOR].

Amarok seems to be saved from the Zombies now thanks to you Mc4Man!
Many thanks!
Phil Smith
Duluthistan, GA

---

