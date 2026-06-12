---
title: "Only using one core of dual core? See picture.."
date: 2009-12-20
forum: New to Ubuntu
---

### Post by vault55 on 2009-12-20
[SIZE=3]I downloaded a benchmarking package and noticed that one core is being stressed. I downloaded this after having some stuttering issues and I knew it wasnt my graphics card.  Ive seen where someone discussed a bug on a different forum but I dont think  its official? Any ideas or help from someone that knows would be appreciated.[/SIZE]

---

### Post by vault55 on 2009-12-21
Can someone please shed some light on this and help me understand why only one core is working.  Is this what it is going to do when I install on a quadcore machine?:confused:

---

### Post by norm7446 on 2009-12-21
Is it just the Benchmark software that is stressing one core only or is it an Ubuntu fault do you think. 

I have an AMD Dual core in my base unit as you can see from the screen shot. Here I'm doing a system test and as you can see it is using both core's.

---

### Post by NoaHall on 2009-12-21
Right click -> Add to panel -> "CPU Frequency Scaler" -> Change the clock to 2800.

---

### Post by vault55 on 2009-12-21
> **norm7446 said:**
> Is it just the Benchmark software that is stressing one core only or is it an Ubuntu fault do you think. 

I have an AMD Dual core in my base unit as you can see from the screen shot. Here I'm doing a system test and as you can see it is using both core's.

Its not a benchmark problem because your having the same problem. One of your cores is working like crazy and the other is lazy.  Just like mine.:confused:

---

### Post by vault55 on 2009-12-21
> **NoaHall said:**
> Right click -> Add to panel -> "CPU Frequency Scaler" -> Change the clock to 2800.

thanks, I will try this out when I get home from the office.

---

### Post by NoaHall on 2009-12-21
You might need to right click on the applet, and change the cpu to "CPU0" or "CPU1"

---

### Post by bodhi.zazen on 2009-12-21
> **vault55 said:**
> [SIZE=3]I downloaded a benchmarking package and noticed that one core is being stressed. I downloaded this after having some stuttering issues and I knew it wasnt my graphics card.  Ive seen where someone discussed a bug on a different forum but I dont think  its official? Any ideas or help from someone that knows would be appreciated.[/SIZE]

[SIZE=10]Please use the default forums font size. If you have a hard time reading, change the settings on your browser[/SIZE]

---

### Post by vault55 on 2009-12-21
> **bodhi.zazen said:**
> [SIZE=10]Please use the default forums font size. If you have a hard time reading, change the settings on your browser[/SIZE]

thanks for your guidance with the issue that Im having and the warm welcome to these forums.

---

### Post by Fire_Chief on 2009-12-21
It is possible that some of the applications you are running are not aware of multiple cores or are single threaded.

---

### Post by Marvin666 on 2009-12-21
It looks like you have dynamic frequency scaling enabled. I've always disabled this from the bios (core[s] always run at full speed). You'd probablly save on power usage in a laptop, or heat if you leave it enabled.

---

### Post by vault55 on 2009-12-21
.

---

### Post by vault55 on 2009-12-21
> **Marvin666 said:**
> It looks like you have dynamic frequency scaling enabled. I've always disabled this from the bios (core[s] always run at full speed). You'd probablly save on power usage in a laptop, or heat if you leave it enabled.

Marvin, I looked for that setting in the BIOS and it dosent exist. (Lenovo ThinkPad T400, 2 weeks old)

---

### Post by synapsys on 2009-12-21
Have you tried opening system monitor and playing around with apps?

I run a quad core with karmic, and some apps will stress one core, while others balance across all 4.

---

### Post by vault55 on 2009-12-21
> **Fire_Chief said:**
> It is possible that some of the applications you are running are not aware of multiple cores or are single threaded.

Im not running anything special that I know of.besides Compiz and my ATI 3470 graphics card (Im new to this so Im not totally proficient yet)

---

### Post by bodhi.zazen on 2009-12-21
> **vault55 said:**
> thanks for your guidance with the issue that Im having and the warm welcome to these forums.

I see you now understand directly how using a large font affects others. Such an effect lowers the chance you will get an answer to your problem.

My grandmother once told me , honey attracts flies better then vinegar and perhaps this advice will help you as well. Keep in mind we are all volunteers here and you are asking a volunteer to offer assistance and you may find revising your posting style will help you get the assistance you desire faster.

To answer your question, I do not think there is anything wrong with the way your system is operating. Linux (Ubuntu) scales back the CPU frequency if you are not doing a task which is CPU intense. This is normal and nothing to be concerned with, although you may wish to tweak your system.

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

[http://www.tectonic.co.za/?p=2560](http://www.tectonic.co.za/?p=2560)

---

### Post by Conzo on 2009-12-21
here's My Cpu use, only have Firefox Running plus what the start up uses

---

### Post by vault55 on 2009-12-21
> **bodhi.zazen said:**
> I see you now understand directly how using a large font affects others. Such an effect lowers the chance you will get an answer to your problem.

My grandmother once told me , honey attracts flies better then vinegar and perhaps this advice will help you as well. Keep in mind we are all volunteers here and you are asking a volunteer to offer assistance and you may find revising your posting style will help you get the assistance you desire faster.

To answer your question, I do not think there is anything wrong with the way your system is operating. Linux (Ubuntu) scales back the CPU frequency if you are not doing a task which is CPU intense. This is normal and nothing to be concerned with, although you may wish to tweak your system.

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

[http://www.tectonic.co.za/?p=2560](http://www.tectonic.co.za/?p=2560)

Well taken and thanks for the reply.  I didnt know it was such a big deal and figured it would probably help those reading (honestly).  Thanks again.

---

### Post by vault55 on 2009-12-21
> **Conzo said:**
> here's My Cpu use, only have Firefox Running plus what the start up uses


Thanks Conzo, I now think this is the norm (as confimed by your picture) I appreciate you taking the time to reply w/ the screenshot.

---

### Post by vault55 on 2009-12-21
Good news, I downloaded all available updates today and it seems whatever update was released today fixed this issue.  (See attached picture)  Thank you to everyone that responded to this issue.

---

