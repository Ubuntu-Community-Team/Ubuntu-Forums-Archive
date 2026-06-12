---
title: "Linux acting choppy"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by nitrousjames on 2009-08-29
Why is Linux suddenly acting choppy?? I changed the background image and the appearance, but now the whole thing is acting choppy. jus a newb here, please help

---

### Post by presence1960 on 2009-08-29
what do you mean by "choppy"? What are you doing when it is "choppy"? What apps are you running when "choppy" happens. What are your system specs. I am afraid you need to provide more specific details about your problem before anyone can even begin to help you.

---

### Post by Wiebelhaus on 2009-08-29
We need system specifications and theme name or other customizations and any other relevant information. Also is this Ubuntu? Have you installed your Graphic drivers?

---

### Post by ad_267 on 2009-08-29
If you're using Ubuntu then System - Administration - System Monitor - Processes will show you if any applications are using a lot of CPU or RAM.

---

### Post by nitrousjames on 2009-08-29
by choppy i mean, wen i scroll down its not continuous, i mean its like stopping for a bit one page and then moving over to the next, wasnt that way earlier.  i use a core2duo 2.1 GHz, 2 gb ram, i allocated 15 gb for linux and about 1.5gb for the swap drive..   i use ubuntu 9.04 jaunty jackalope

tried system=>administration=> system monitor 
lots of stuff there that i cant even comprehend what the apps are for. dont wanna do something stupid and stop the important processes...

---

### Post by mbsullivan on 2009-08-30
> 
tried system=>administration=> system monitor
lots of stuff there that i cant even comprehend what the apps are for. dont wanna do something stupid and stop the important processes...

I think the previous user was asking you to post information about your CPU and memory usage. Approximations of both can be found from the "Resources" tab in the system monitor. You shouldn't have to halt any processes.

Like Wiebelhaus said, this sounds most like a system where the drivers for your graphics card are not optimally installed. Do you know what kind of graphics card you have?

If no, the following might give us a clue. Could you post the output of:

```
sudo lshw | grep display -A 10
```

Mike

---

### Post by nitrousjames on 2009-08-30
> **mbsullivan said:**
> I think the previous user was asking you to post information about your CPU and memory usage. Approximations of both can be found from the "Resources" tab in the system monitor. You shouldn't have to halt any processes.

If no, the following might give us a clue. Could you post the output of:

```
sudo lshw | grep display -A 10
```Mike


i put that code in the terminal and this is what i got back :
*-display UNCLAIMED
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0

and as for the resources tab thing, it says i am using 23% of ram.....

---

### Post by credobyte on 2009-08-30
What if you disable desktop effects ?

---

### Post by mbsullivan on 2009-08-31
> and as for the resources tab thing, it says i am using 23% of ram..... 

Is CPU usage okay?

> product: 82945G/GZ Integrated Graphics Controller
vendor: Intel Corporation

Some Intel graphics cards are having issues with the drivers available in Jaunty, honestly. See [here]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance") to try and troubleshoot yours. 

Rolling back to those in use with Intrepid might give slightly better performance. There are directions on how to do so [here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").

Note that this is a fairly advanced issue to troubleshoot... Sorry :(
Mike

---

### Post by nitrousjames on 2009-09-03
no problems, linux is acting fine at the moment, tried keeping the graphics thing to normal and not high. it worked, thanks for all the help guys

---

