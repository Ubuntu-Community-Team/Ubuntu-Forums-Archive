---
title: "temporarily disable pulseaudio in 9.04"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by ayu on 2009-05-31
Hello,
I think pulseaudio is causing some troubles on my system (a program which should only use 30% of my cpu is now using 70% after "upgrading" to 9.04), and I would like to temporarily disable it before completely removing/uninstalling pulseaudio. In the past, I was able to killall pulseaudio. But when I try that now, it respawns automatically when sound is outputted. I've changed System/Preferences/Sound to alsa for everything already. Is there a way to disable pulseaudio without removing it completely?
Thanks,
Ayu

---

### Post by jerrrys on 2009-06-01
[attach]116098[/attach]

---

### Post by ayu on 2009-06-02
> **jerrrys said:**
> 
[http://ubuntuforums.org/showpost.php?p=4844334&postcount=17](http://ubuntuforums.org/showpost.php?p=4844334&postcount=17)
[QUOTE=Fred_E _krugar;4844334]An easy way to disable PulseAudio is to go into the system monitor and turn off PulseAudio Server. Alsa will then take over.
[/QUOTE]
> **ayu said:**
> In the past, I was able to killall pulseaudio. But when I try that now, it respawns automatically when sound is outputted.

If by system monitor and "turn off", you mean stop the process, yes, I've tried that already. The problem is pulseaudio restarts automatically after starting any program that needs sound.

Thanks,
Ayu

---

### Post by nandemonai on 2009-06-02
> **ayu said:**
> If by system monitor and "turn off", you mean stop the process, yes, I've tried that already. The problem is pulseaudio restarts automatically after starting any program that needs sound.

Thanks,
Ayu

```
sudo /etc/init.d/pulseaudio stop
```

That do it? (I can't test at the moment unfortunately).

---

### Post by jerrrys on 2009-06-02
[ATTACH]116171[/ATTACH]

and im finding this at...

[http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS279&=&q=temporarily+disable+pulseaudio+in+9.04&btnG=Google+Search&aq=f&oq=](http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS279&=&q=temporarily+disable+pulseaudio+in+9.04&btnG=Google+Search&aq=f&oq=)

---

### Post by ayu on 2009-06-02
> **nandemonai said:**
> ```
sudo /etc/init.d/pulseaudio stop
```

That do it? (I can't test at the moment unfortunately).

That doesn't do it for me. But I get the message:
```
ayu@ubuntu:~$ sudo /etc/init.d/pulseaudio stop
 * PulseAudio configured for per-user sessions
```
What does per-user sessions mean?



> **jerrrys said:**
> [ATTACH]116171[/ATTACH]

and im finding this at...

[http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS279&=&q=temporarily+disable+pulseaudio+in+9.04&btnG=Google+Search&aq=f&oq=](http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS279&=&q=temporarily+disable+pulseaudio+in+9.04&btnG=Google+Search&aq=f&oq=)

This looks like removing pulseaudio - not temporarily disabling it. By the way, could you use quote in the future instead of doing a screenshot of text?

Thanks,
Ayu

---

### Post by jerrrys on 2009-06-02
nah :)  and good luck...

---

### Post by braete on 2009-06-02
pasuspender ?
add it at the beginning (in terminal or in launcher)

 
i use that to temporary suspend pulse while playing a wine game.
when i close the game, pulse is again on

---

### Post by ayu on 2009-06-02
> **braete said:**
> pasuspender ?
add it at the beginning (in terminal or in launcher)

 
i use that to temporary suspend pulse while playing a wine game.
when i close the game, pulse is again on

Hm, interesting. Never would have thought such a program exists. I will try that when I have the chance.

Thanks, 
Ayu

---

### Post by braete on 2009-06-02
> **ayu said:**
> Hm, interesting. Never would have thought such a program exists. I will try that when I have the chance.

Thanks, 
Ayu

you dont have to download anyting ( i think it comes with pulse ...)

you just add that at the begineing of the command line/ launcher line

---

### Post by ayu on 2009-06-02
> **braete said:**
> you dont have to download anyting ( i think it comes with pulse ...)

you just add that at the begineing of the command line/ launcher line

Yeah I know. It just feels like the developers were expecting to break programs so they had to write another to disable pulseaudio :p

Thanks again, 
Ayu


Update:
Finally had the time to test it out: pasuspender does not work; pulseaudio starts up automatically anyways :(

---

### Post by ayu on 2009-06-08
Bump!

---

### Post by kay-man on 2009-06-08
in /etc/pulse/client.conf there is a setting autospawn. You can set it to no and then kill pulseaudio. Or maybe restart the init.d script first so it reads the file. I can't test it because in the end i uninstalled pulseaudio completely. Fortunately the .conf file is still there :)

---

### Post by markbuntu on 2009-06-08
I found autospawn set to on in etc/default/pulseaudio.

---

### Post by ayu on 2009-06-09
> **kay-man said:**
> in /etc/pulse/client.conf there is a setting autospawn. You can set it to no and then kill pulseaudio. Or maybe restart the init.d script first so it reads the file. I can't test it because in the end i uninstalled pulseaudio completely. Fortunately the .conf file is still there :)

Thank you thank you thank you! :)

Setting autospawn to no in client.conf works. I am now sure pulseaudio is causing the trouble; the program uses 25% cpu at 800MHz vs 65% at 1600MHz with pulseaudio. But now it is easy to control when pulseaudio is on or off, so I might leave it installed.

---

### Post by alexei.colin on 2009-12-20
> **braete said:**
> pasuspender ?
add it at the beginning (in terminal or in launcher)

 
i use that to temporary suspend pulse while playing a wine game.
when i close the game, pulse is again on

Thank you! pasuspender works great! The problem with killing and restarting pulseaudio process in 9.10 for me was the several annoying side effects (loss of volume systray icon, muting in one of the many sound output leve controls). pasuspender is a nice clean solution. I'm also using it with wine game.

---

