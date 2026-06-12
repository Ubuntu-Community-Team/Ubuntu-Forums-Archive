---
title: "System data"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by arno48 on 2011-06-22
What have I to type in terminal to find out my system data, i.e Processor, RAM, etc.?
Thanks

---

### Post by jmszr on 2011-06-22
arno48,

This will show you in the terminal:

```
sudo lshw
```

or, that information in a file on your desktop:

```
 sudo lshw -html > ~/Desktop/hardware.html
```

Hope that helps.

---

### Post by arno48 on 2011-06-22
> **jmszr said:**
> arno48,

This will show you in the terminal:

```
sudo lshw
```or, that information in a file on your desktop:

```
 sudo lshw -html > ~/Desktop/hardware.html
```Hope that helps.

Thank you very much.
First command is perfect.
I tried the second one too (including in the short version
 
[CODE]sudo lshw -html [CODE] )
but this one does not work.
it appears :
></tr><tr><td class="sub-first"> memory</td><td>:</td><td>fdee0000-fdeeffff</td></tr><tr><td class="sub-first"> memory</td><td>:</td><td>febe0000-febfffff</td></tr></table></td></tr>
 </tbody>             </table></div>
             </div>
(To be continued for pages)

---

### Post by jmszr on 2011-06-22
arno48,

I don't know what to tell you; I just ran that command three times in my terminal and all three times it put a hardware info file on my desktop.

Did you copy and paste the command, or retype it?

---

### Post by e79 on 2011-06-22
```
sudo apt-get install hardinfo
```

This would install the 'System profiler and benchmark' from the Ubuntu Software Center, wrapping all the required information into a nice GUI (as shown on the screenshot).

Enjoy :P

e79

---

### Post by arno48 on 2011-06-22
> **jmszr said:**
> arno48,

I don't know what to tell you; I just ran that command three times in my terminal and all three times it put a hardware info file on my desktop.

Did you copy and paste the command, or retype it?

When I type
sudo lshw -html > ~/Desktop/hardware.htmlThe answer is 
File or directory not existing.

Thanks for your time.

---

### Post by e79 on 2011-06-22
I tried this '**sudo lshw -html > ~/Desktop/hardware.html**'  proposed by '**jmszr**' and it worked perfectly for me....copy/pasting it and typing it manually...If it still does not work refer to my post regarding 'hardinfo'.

---

### Post by arno48 on 2011-06-22
> **e79 said:**
> ```
sudo apt-get install hardinfo
```This would install the 'System profiler and benchmark' from the Ubuntu Software Center, wrapping all the required information into a nice GUI (as shown on the screenshot).

Enjoy :P

e79
Thanks
I copied and pasted, and I think that    hardinfo  has been installed.
However I am not able to open it, 
I looked for it either in Ubuntu Software Center and in Synaptic.
Where is the mistake of mine?

---

### Post by e79 on 2011-06-22
> **arno48 said:**
> Thanks
I copied and pasted, and I think that    hardinfo  has been installed.
However I am not able to open it, 
I looked for it either in Ubuntu Software Center and in Synaptic.
Where is the mistake of mine?

Once installed, it should be in your 'System Tools' menu :

Open **Applications --> System Tools --> System Profiler and Benchmark**

If you still cannot find it, simply open a Terminal and type :
```
hardinfo
```and press Enter :p

---

### Post by arno48 on 2011-06-22
> **e79 said:**
> ```
sudo apt-get install hardinfo
```This would install the 'System profiler and benchmark' from the Ubuntu Software Center, wrapping all the required information into a nice GUI (as shown on the screenshot).

Enjoy :P

e79

I succeess to open it though Launcher,  
It really very, very well done.
Thank you very much

---

### Post by wildmanne39 on 2011-06-22
Hi, I suspect it is because he is running natty, like I am. I tried that command and it just sat there and put out no data, of course it could be something to do with our computers.

---

### Post by e79 on 2011-06-22
> **arno48 said:**
> I succeess to open it though Launcher,  
It really very, very well done.
Thank you very much

The pleasure is all mine  :P

[QUOTE=wildmanne39]Hi, I suspect it is because he is running natty, like I am. I tried that  command and it just sat there and put out no data, of course it could  be something to do with our computers. 	[/QUOTE]

I tried it on my laptop on which I installed Natty (11.04 amd64) and also tested it into a Maverick (10.10 i386) edition and both worked like a charm, must be something on your PC indeed...

---

### Post by arno48 on 2011-06-23
> **wildmanne39 said:**
> Hi, I suspect it is because he is running natty, like I am. I tried that command and it just sat there and put out no data, of course it could be something to do with our computers.

Hi,
Do type      hardinfo     in Launcher.

It's really worthwhile.

Please tell me when you succeed, so I can match this thread as SOLVED

---

### Post by arno48 on 2011-06-26
Dear jmszr, Dear e79,
Thanks for your help, now I can mark this thread as solved

---

