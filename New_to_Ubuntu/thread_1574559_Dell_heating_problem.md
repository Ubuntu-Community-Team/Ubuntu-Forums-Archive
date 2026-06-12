---
title: "Dell heating problem"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by beew on 2010-09-14
Hi,

I  have lucid installed on an old Dell latitude D410 laptop. This is one of those models that generate a lot of heat  ( Dell has been sued for that or similar models because of overheating). When I had windows XP installed I used the i8k Dell fan to cool it somewhat. In Ubuntu I  use gkrellm- i8k to do the job (but I have to download the .deb package manually as it was somehow removed from the Ubuntu repo,--but it is still in the Fedora repo)

Now the  problem is that while gkrellm is pretty it itself uses a lot of cpu and generates heat. I am wondering if there is  a way to run i8k without gkrellm (I couldn't find any unfortunately) or other alternatives to i8k.

Thanks.

---

### Post by JohnHeikkila on 2010-09-14
Install i8kutils to access the **i8kfan**-program.
```
sudo apt-get install i8kutils
```

---

### Post by beew on 2010-09-14
i8kutils is already installed. How do you configure it without gkrellm?

---

### Post by beew on 2010-09-26
bump??

---

### Post by sandyd on 2010-09-26
> **beew said:**
> i8kutils is already installed. How do you configure it without gkrellm?
```

sudo nano /etc/default/i8kmon

```
change it to "1" to enable it
```

/etc/default/i8kbuttons 

```
change it to 1 to enable it as well.

restart
```

i8kmon --auto
```

---

### Post by Kixtosh on 2010-09-26
I have similar concerns with a totally different laptop. Would you mind explaining what you mean by "heating problem", how you measured it to begin with, and what you are doing about it?

Maybe I could use some of the suggestions being made here, or I might also start another thread if it turns out that I may have valid concern, but I'd like to hear about your experience with the problem before investigating further what, if anything, I need to do about it.

---

### Post by Arex Bawrin on 2010-09-26
I've also had this problem with my Dell M1710 on the last 3 releases of Ubuntu (on Lucid now). The M1710 is a resource hog, but it was clearly cooler in Windows when I was dual-booting. Any suggestions would be appreciated.

---

### Post by Arex Bawrin on 2010-09-26
Duplicate. Sorry my browser messed up.

---

### Post by Arex Bawrin on 2010-09-26
Duplicate.

---

### Post by Arex Bawrin on 2010-09-26
Duplicate.

---

### Post by beew on 2010-09-26
sandyd

Thanks for the reply, I will give it a try later.

---

### Post by beew on 2010-09-26
> **Kixtosh said:**
> I have similar concerns with a totally different laptop. Would you mind explaining what you mean by "heating problem", how you measured it to begin with, and what you are doing about it?

Maybe I could use some of the suggestions being made here, or I might also start another thread if it turns out that I may have valid concern, but I'd like to hear about your experience with the problem before investigating further what, if anything, I need to do about it.

The temperature of the cpu constantly hovering around 60C and if some apps are running it can rise to 70C or even 90C. Even if nothing is running it is above 50C. Apparently it is due to a design flaw of some Dell laptops and it had been sued over that. 

I use the i8K module to control the fan. This is specially designed for some Dell models so I don't know what you can do with overheating for something that is not Dell.

---

### Post by beew on 2010-09-26
> **Arex Bawrin said:**
> I've also had this problem with my Dell M1710 on the last 3 releases of Ubuntu (on Lucid now). The M1710 is a resource hog, but it was clearly cooler in Windows when I was dual-booting. Any suggestions would be appreciated.

For my Dell D410 it is just as hot in Windows XP and I also use i8k to control the temperature. Dell's heating problem has nothing to do with Ubuntu, it is the same in Windows. I used to have a Dell Inspiron 8500 running XP only, it was even hotter, I didn't need heating in my room in the winter if I just left it on, it got a bit better after I installed i8k.i8k is actually a windows program written specifically to deal with that, it was only later ported to Linux.

The difference is in Windows i8k is a stand alone app and running it doesn't cost as much resources as in Ubuntu since I have to run it through gkrellm which itself hogs quite a bit of CPU. I will try SandyD's suggestion to see if I can run i8k alone.

---

### Post by Kixtosh on 2010-09-27
> **beew said:**
> The temperature of the cpu constantly hovering around 60C and if some apps are running it can rise to 70C or even 90C. Even if nothing is running it is above 50C. Apparently it is due to a design flaw of some Dell laptops and it had been sued over that. 

I use the i8K module to control the fan. This is specially designed for some Dell models so I don't know what you can do with overheating for something that is not Dell.Very interesting, thanks for the response. I'm running two Toshiba Portégé ultra-portables. One is an ancient 3490CT that usually runs around 45-55°C, according to the included panel applet I use in Xubuntu (with the LXDE desktop environment - which makes it run much faster despite the limited resources). I actually don't hear the fan working much usually on that unit. The other is a much newer Portégé R205 from around 2007, and it runs mostly around 60-65°C. Surprisingly (at least I thought so), I hardly hear the fan working (never ever at 60°C, for instance), which I have been wondering about. If I use something like YouTube, then it goes right up to 75°C and the fan finally really speeds up. I've never seen it go above that temperature, though, but that still seemed pretty hot to me (hence my interest in this thread).

For the R205, which is running Ubuntu Lucid Lynx, I'm using the GNOME Sensors Applet 2.2.3 that I was able to add after adding a few extras, including the System Profiler and Benchmark from the Ubuntu Software Center. I did notice that the fan seems to work far harder and far more often in Windows XP than with Ubuntu, so I've sometimes wondered whether Win XP is making the unit run hotter more often, or is Win XP simply turning the fan on more often and at lower temperatures than Ubuntu.

Well, since I can't use the same tools to figure this out, I'll leave your thread alone (except to follow any developments), but it sounds as though I should really figure out whether 75°C is a normal working temperature for the Portégé or whether I should be searching for a method to turn the fan on earlier and more often (or stick to using the dastardly Windows XP Pro!).

---

### Post by madmax75 on 2010-09-28
> **beew said:**
> The temperature of the cpu constantly hovering around 60C and if some apps are running it can rise to 70C or even 90C. Even if nothing is running it is above 50C. Apparently it is due to a design flaw of some Dell laptops and it had been sued over that.

I use **cpulimit** to curb individual apps from hogging the cpu and ending up heating it too much (I'm on a laptop - those are not very nice when it comes to venting extra heat out).

This is the command I use with it:

```
sudo cpulimit --pid PROCESS_ID_NUMBER --limit 55
```

--pid PROCESS_ID_NUMBER:

Obviously you need to replace the PROCESS_ID_NUMBER with the PID number of the offending process. You can find this out with the** top** command.

--limit 55:

This is the percentage of the cpu you allow the process to use. In the example I do not allow the process to use more than 55 percent of the cpu. You can tweak the value to your liking.

For me, this works wonders. I let cpulimit run in a terminal and I can use programs that used to cause my laptop cpu fan to cry for help.

---

