---
title: "Amount of RAM in ubuntu"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by yotyoter on 2011-07-01
Will some one please tell me how to check the amount of ram I have in Ubuntu? I know how to do it in Windows, but I don't know where it is in Ubuntu. Is there a command or a graphic display? (Both would be nice.)

---

### Post by androssofer on 2011-07-01
open a terminal and type 
```

top
```

this shows lots of info, but ram is in ther sumwer haha


or open system monitor, system >> admin >> sytem monitor.. then click the "resources" tab

or if using unity just search for "system monitor" :-)

---

### Post by Laforge129 on 2011-07-01
> **yotyoter said:**
> Will some one please tell me how to check the amount of ram I have in Ubuntu? I know how to do it in Windows, but I don't know where it is in Ubuntu. Is there a command or a graphic display? (Both would be nice.)

I don't know what they call it on the Ubuntu side but you can find out how much memory you have by using Kinfocenter(Kubuntu version name) probably ginfocenter(for Ubuntu).  You should be able to find it under Applications > System or at least that is how I found it myself!

---

### Post by deconstrained on 2011-07-01
There's a nice GUI hardware profiler available for Ubuntu and Linux in general if you want to get really into detailed system specs (I forgot what it's called), but the fastest way to get information on total memory in the system is to open up a terminal and type the command "free". Use it with the "-m" flag to set the units to megabytes.

Also, how 'bout putting this in your ~/.bashrc file:
```
alias topmemusage='ps aux | awk '\''{if ( $4 >= 0.5 ) printf $4/100*4096 "\tMB\t" $11 "\n"}'\'' | sort -h'
```
Invoking that alias will display all processes consuming over 0.5% of your total memory and print them in ascending order with their respective memory consumption in megabytes.

**EDIT: Whoops, I forgot that when I wrote that long ago I had hard-coded the physical size of my memory into that alias. replace "$4/100*4096" with "$6/1024"**

---

### Post by mcduck on 2011-07-01
System Monitor is installe din Gnome by default, and displays the amount of available & used RAM.

For more details about memory usage, you might want to pop open a terminal and run "free -m" or "top". "cat /proc/meminfo" would give pretty detailed info about the installed memory modules themselves.

---

### Post by haqking on 2011-07-01
[COLOR=#c20cb9][/COLOR]grep MemTotal /proc/meminfo

or free-m

Edit: ooh didnt see post above when posting, ninja'd ;-)

---

### Post by alphacrucis2 on 2011-07-01
A useful method of getting everything you want to know (or didn't want to know ;) ) about your pc is this command:

```
sudo lshw -html > MyPcHardware.html
```

That will create a full report on your hardware and write it as a file in html format. You would then find this file "MyPcHardware.html" in nautilus and double click on it to display it in you web browser.

---

### Post by SeijiSensei on 2011-07-01
"cat /proc/meminfo" will tell you everything you want to know about memory usage and more.

---

### Post by collisionystm on 2011-07-01
Or you can install htop

```
sudo apt-get install htop
```
```

htop
```

---

### Post by jerome1232 on 2011-07-01
Unity - Click shutdown, System Settings, System Monitor

Classic Gnome - System, Administration, System Monitor

---

### Post by CVGH on 2011-07-01
> **deconstrained said:**
> 
Also, how 'bout putting this in your ~/.bashrc file:
```
alias topmemusage='ps aux | awk '\''{if ( $4 >= 0.5 ) printf $4/100*4096 "\tMB\t" $11 "\n"}'\'' | sort -h'
```

Nice!!!!

---

### Post by deconstrained on 2011-07-02
> **CVGH said:**
> Nice!!!!

see edit of original post.

---

### Post by donny.davis on 2011-07-02
one more better option is tht u can download Sysinfo
its a good software to view details of ur system

u can use the software centre
or do a command install
```

sudo apt-get install sysinfo
```

chk this out
[http://www.ubuntugeek.com/howto-get-your-system-information-with-sysinfo.html](http://www.ubuntugeek.com/howto-get-your-system-information-with-sysinfo.html)

---

### Post by amjjawad on 2011-07-02
> **mcduck said:**
> System Monitor is installe din Gnome by default, and displays the amount of available & used RAM.


+1 and it's fair enough as a first choice.

---

### Post by Kixtosh on 2011-07-02
> **amjjawad said:**
> +1 and it's fair enough as a first choice.Absolutely. There's no need to look any further for something as simple as RAM.

Otherwise (for more information about other things) along with the other options suggested, there is also the System Profiler and Benchmark. It's available from the Ubuntu Software Center and is included by default, instead of System Monitor, in some of the LXDE distros I have used (or still use), so I like to add it in Ubuntu as well. Once installed, it can be found in the "System Tools" menu of the "Applications" drop down menu in the Top Panel.

I particularly liked the ease of using this method suggested earlier by **alphacrucis2**:

```
sudo lshw -html > MyPcHardware.html
```It takes seconds to complete, and actually leaves a permanent HTML document in the user's /Home directory. This can be "clicked" at any time for future reference, opening in a browser window (unless something in the system has changed, in which case it would have to be run again to generate a new system "snapshot").

---

### Post by dFlyer on 2011-07-02
> **yotyoter said:**
> Will some one please tell me how to check the amount of ram I have in Ubuntu? I know how to do it in Windows, but I don't know where it is in Ubuntu. Is there a command or a graphic display? (Both would be nice.)

From a terminal enter:

free -tom

---

