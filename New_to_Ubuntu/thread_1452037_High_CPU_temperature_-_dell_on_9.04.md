---
title: "High CPU temperature - dell on 9.04"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Boulemans on 2010-04-11
My CPU temperature gets easily very high: now its core temperature around 50 °C and when playing a game its getting close to 100°C, with a system shutdown as a result very easily. I measure it with lm sensors ...

The question: How can I reduce this temperature? With windows it wasn't that high :-( Now with linux, i can't even play a decent game of wormux or so without risking a shutdown ...

system spec: dell vostro 1000, dual core and 64 bit ubuntu 9.04 installation.

---

### Post by stilling on 2010-04-11
i know that all system in their motherboard bios hasan option that can increase the speed of the processor cooler or can be set to auto, auto means that he starts to spin faster when the processor is more hot and slower when is cooled so my answer reboot press f2 to go to bios search that option and select to always spin you will know what i say when you will see and that will reduce your processor heat or you can open your pc and clean the dust from the cooler posibly he cant throw away the heat

scuse my english

hope this helps

---

### Post by nema.arpit on 2010-04-11
You can try undervolting.
Look up linux-phc (processor hardware control) or any other appropriate tool.

However it is more than likely a problem with your linux setup or the game you are running,considering it ran cool in windows.

---

### Post by thenailedone on 2010-04-11
Or maybe Windows or Ubuntu u is showing the wrong temps... have you looked at your CPU load under Ubuntu... is it staying high (and if it is, have you run any CPU intense applications under Windows to simulate it because 100 degC on a CPU is madness...)

---

### Post by no2498 on 2010-04-11
open a terminal type,htop and or top
it tells you how to install them
type htop or top what ever 1 you loaded see see what is running

hope this helps

---

### Post by Boulemans on 2010-04-12
Now I've read that Dell has a few problems with fan control. But I hear my fan's running (strange?)

It's just that when playing or running a program that is just that little bigger, my laptop shuts up.

My dual core CPU is now running 15%  15%, while just a sec ago it was 40 - 90 % of the CPU :s

I'm just tired of these shutdowns ... i cant even watch a movie whit this.

I didn't found any entry in the bios about Fan speed.

For the record: it is a Dell Vostro 1000 laptop, so removing the case is not a real solution here :-)

---

### Post by J V on 2010-04-12
Not sure what exactly the problem is, but heres an idea: Take a hoover to the inside of your computer (And attach a pen shell to the end with duck tape to get deeper into the processor)

---

### Post by Boulemans on 2010-05-14
I've learned that powernow-k8 could give a solution. Can Someone give a full explenation how to use this driver? I've searched via google and found lots of problems, but no stand alone install faq or something like that...

---

### Post by consindo on 2010-05-14
I have a Dell and it had a high temp. If you clean out all the dust it might help. Worked for me. :)

---

