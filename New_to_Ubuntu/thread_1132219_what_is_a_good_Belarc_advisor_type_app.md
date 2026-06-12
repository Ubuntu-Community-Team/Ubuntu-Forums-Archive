---
title: "what is a good Belarc advisor type app?"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by bu2971x on 2009-04-21
whats a good app like Belarc advisor to show everything about
your computer that works in 8.04 and fox 3.

---

### Post by supersonicdarky on 2009-04-21
There isn't really any one app that can bring all info together like that and out put it into a file. There is an app to view info (and benchmark some things) but I can't recall its name.

But if there's a demand I can write a bash/python script for it.

---

### Post by halitech on 2009-04-21
why not just open a terminal and type in
```
lshw  >> ~/hardware.txt
```

will create a text file in your home folder that you can read in notepad

---

### Post by supersonicdarky on 2009-04-21
I assumed (s)he wanted something human-readable. lshw is rather advanced.

---

### Post by halitech on 2009-04-21
could be right but lshw is complete if nothing else :)

---

### Post by LindaLou on 2009-04-22
I'm in need of a Belarc similar application as well. ([www.belarc.com/free_download.html](www.belarc.com/free_download.html))
I used this dowload with Windows and it was extremely useful.  With the use of Belarc I found out that I had an antique processor (and I do mean antique) installed when in fact I had paid for a new processor that would be identical to the original. Because of Belarc, I was able to prove this con job with the print out in layman terms, and receive the processor that I requested.

So, yes, supersondicdarky, there could be a demand for the application
> But if there's a demand I can write a bash/python script for it. 

---

### Post by supersonicdarky on 2009-04-22
Alright, I'll get started on it. May take a few days, if you don't mind (busy with other things).

Perhaps eventually it'll grow into something big

---

### Post by bu2971x on 2009-04-23
good one

---

### Post by LindaLou on 2009-04-24
> Alright, I'll get started on it. May take a few days, if you don't mind (busy with other things).

Perhaps eventually it'll grow into something big


That's great!! Appreciated. Looking forward to your results.

---

### Post by Grumpster on 2009-10-21
Any update on this yet? This is something I could really use right now. I need a way to identify all of my hardware, networks, etc like the[FONT=Arial][SIZE=1] [/SIZE][/FONT]Belarc Advisor[SIZE=2] [/SIZE]does.

---

### Post by winotree on 2009-10-21
**hardinfo** is nowhere near as good but it's in the repositories -- maybe take a look at it.

---

### Post by Sir Jasper on 2009-10-21
Hi,

I may well be wrong but I have a vague recollection that it (BA) works in Wine.

My regards

---

### Post by Gwasanaethau on 2009-10-21
> **winotree said:**
> **hardinfo** is nowhere near as good but it's in the repositories -- maybe take a look at it.
I was going to suggest **hardinfo** too. I don't know about it not being as good – it seems to have all of the features that Belarc has, except (obviously) the things that are Windows specific, such as the security update list. It also doesn't have a list of programmes and their access times, but I'm sure there's some command in aptitude or synaptic that will provide that info if you need it.

---

### Post by Grumpster on 2009-10-22
I'm not worried about the software issues. I'm looking only at the hardware in the system. I'll give advisor a try under wine. Wouldn't expect it to work, but who knows. I'll let y'all know how it works. I did give hardinfo a try and it didn't do so well. It shows what Linux video drivers are being used instead of the actual video card installed for example. Hopefully advisor will work. It gives the accurate info I need.

---

### Post by louieb on 2009-10-22
Take the output of lshw, convert to html, put it in a file, display the file in firfox.

```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html 
```

---

### Post by winotree on 2009-10-22
**louieb**, that is as nice a solution as I've seen since I can't remember when!  :D  I've bookmarked your solution -- *just after running the code and bookmarking it*.  ;)

---

### Post by dutty on 2010-01-26
[SIZE=3][FONT=Comic Sans MS]H[/FONT][/SIZE]i!

I am an obvious Ubuntu newbie. When I pasted in 
lshw  >> ~/hardware.txt






[LEFT]
[/LEFT]

I was to to run the program as a super user. Does that mean using # 

Thanks. I was trying to use Belarc too. Great program! :D

---

### Post by dutty on 2010-01-26
> **louieb said:**
> Take the output of lshw, convert to html, put it in a file, display the file in firfox.

```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html 
```

Thanks for the info, it proved very useful.:)

---

### Post by kimberlite on 2010-01-26
geekbench can be a useful tool, when you want to compare your hardware performance to others': [http://www.primatelabs.ca/geekbench/]("http://www.primatelabs.ca/geekbench/") Free trial version running from terminal.

---

