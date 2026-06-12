---
title: "Downloading software problems"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by MoonWolf85 on 2009-05-13
If anyone could explain this to me, I would really appreciate it. 

I started downloading Frostwire, but half-way through the installation my laptop froze and had to be restarted. Since then, I can't download anything. I can't download Frostwire, even software updates. 

When I try to install software updates I get this error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I try to install the Frostwire package, I get told that only one software management tool can be in use at a time and I need to shut down the other software management tool, but there isn't another tool running. 

If anyone can help me out, I would be really grateful. My little brother build this system up and I don't understand much of it. I showed him everything and he just shrugged and said he didn't know what to do at all. 

Help?

---

### Post by mikewhatever on 2009-05-13
Make sure you close Synaptic and Add/Remove, then run **sudo dpkg --configure -a** in Terminal.

---

### Post by Bodsda on 2009-05-13
Hi,

Welcome to the forums.

The problem is with the package manager and was probably caused by the incomplete install you mentioned. If we take a look at the first line of error message
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Now, 'dpkg was interrupted' which basically means the package manager was working on the package and then it was halted and could not terminate properly. The next bit is important as it tells us what to do
```
you must manually run 'dpkg --configure -a' to correct the problem
```
This means that we should execute the command it mentions, in a terminal. So open a terminal 

Applications >> Accessories >> Terminal

and type/copy the following command
```
sudo dpkg --configure -a
```

This should fix your problem. I recommend you run this command before installing anything else

```
sudo apt-get update && sudo apt-get upgrade
```

Hope this helps,

Regards,

Bodsda

p.s: If you need anymore clarification or have another question, please dont hesitate to ask.

---

### Post by MoonWolf85 on 2009-05-13
That last post was extremely helpful. I believe I got everything installed. The problem now being that I can't find the actual Frostwire program, only all the individual files. Thus I can't figure out how to run Frostwire now that I have it installed.

---

### Post by dr.pepper23 on 2009-05-13
Hey. You should be able to just type frostwire in the terminal to run it. If I'm not mistaken, the files are probably in /usr/bin, but I could be wrong. It thats not correct, try looking around in those folders. Hope this helped.

---

### Post by MoonWolf85 on 2009-05-13
I did actually think of typing 'frostwire' in terminal and this came up... 

jen@robbie-laptop:~$ frostwire
Error: Could not open jar file: jython.jar
Traceback (most recent call last):
  File "/usr/lib/frostwire/unpack200.py", line 57, in <module>
    unpack200()
  File "/usr/lib/frostwire/unpack200.py", line 53, in unpack200
    os.remove(f)
OSError: [Errno 13] Permission denied: 'jython.pack'
HOSTNAME IS robbie-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_07]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./jython.jar
Unable to access jarfile FrostWire.jar


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

jen@robbie-laptop:~$ 




None of which makes much sense to me.

---

### Post by linux_holic on 2009-05-13
firstly, check your internet connection...... (i think that is important) 

and, check your commands.....

i hope it will help you...

---

### Post by Ragnar Bocephus on 2009-05-13
Can you try 

```
sudo frostwire
```

and see if it works then?  If so, there's a permissions issue somewhere...

---

### Post by MoonWolf85 on 2009-05-13
> **Ragnar Bocephus said:**
> Can you try 

```
sudo frostwire
```and see if it works then?  If so, there's a permissions issue somewhere...


That seems to have worked! You people are awesome. Thank you!

---

### Post by -kg- on 2009-05-13
I just looked up what frostwire is, and it is a P2P software (which I'm sure you know, but others who read this may not).  I *_seriously_* would not run this software using sudo, and would seriously hesitate running it with gksu.

You need to look into your permissions issue and resolve that, making the program run normally without full access to root.

---

### Post by geoffree on 2011-11-24
I had a similar problem and solved it with your advice.  11/24/11.
Nothing is ever lost.
Thanks,
G




> **Bodsda said:**
> Hi,

Welcome to the forums.

The problem is with the package manager and was probably caused by the incomplete install you mentioned. If we take a look at the first line of error message
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Now, 'dpkg was interrupted' which basically means the package manager was working on the package and then it was halted and could not terminate properly. The next bit is important as it tells us what to do
```
you must manually run 'dpkg --configure -a' to correct the problem
```
This means that we should execute the command it mentions, in a terminal. So open a terminal 

Applications >> Accessories >> Terminal

and type/copy the following command
```
sudo dpkg --configure -a
```

This should fix your problem. I recommend you run this command before installing anything else

```
sudo apt-get update && sudo apt-get upgrade
```

Hope this helps,

Regards,

Bodsda

p.s: If you need anymore clarification or have another question, please dont hesitate to ask.

---

