---
title: "installing teamspeak 3"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Existance0 on 2010-04-26
I was wondering if someone could help me install teamspeak 3. I tried using the package manager but it installs teamspeak 2. I downloaded the .run package from their website and it extracted a folder to my desktop but I don't know what to do with it I tried to run almost every file in the main directory but none of them seemed to do anything.

---

### Post by Existance0 on 2010-04-27
bump

---

### Post by Jon Monreal on 2010-04-27
> **Existance0 said:**
> I was wondering if someone could help me install teamspeak 3. I tried using the package manager but it installs teamspeak 2. I downloaded the .run package from their website and it extracted a folder to my desktop but I don't know what to do with it I tried to run almost every file in the main directory but none of them seemed to do anything.

Hello,

You should be able to follow [these instructions]("https://help.ubuntu.com/community/InstallingRunPackage") to install Teamspeak.

If you need additional help, please feel free to ask.

---

### Post by Existance0 on 2010-04-28
> **Jon Monreal said:**
> Hello,

You should be able to follow [these instructions]("https://help.ubuntu.com/community/InstallingRunPackage") to install Teamspeak.

If you need additional help, please feel free to ask.

I already read that and followed those instructions all the installer did was extract a folder to my desktop that I can't do anything with.

---

### Post by Jon Monreal on 2010-04-28
Double-click on the file "ts3client_runscript.sh" in the folder and select "Run".

---

### Post by Existance0 on 2010-04-28
Nothing happens.

---

### Post by Jon Monreal on 2010-04-28
> **Existance0 said:**
> Nothing happens.

Nothing happens after you select "Run", or you never get the option to select "Run"?

At any rate, you could try opening a terminal (Applications -> Accessories -> Terminal), changing directory to the folder in question, then typing
```
./ts3client_runscript.sh
```
pressing enter, and then copy+pasting what it says and posting it here. If you need further assistance doing this, please feel free to ask.

---

### Post by Existance0 on 2010-04-28
```
cd arie@DT:~$ cd /home/arie/Desktop/TeamSpeak3-Client-linux_x86
arie@DT:~/Desktop/TeamSpeak3-Client-linux_x86$ ./ts3client_runscript.sh
2010-04-28 09:21:24.095340|INFO    |MPSingleton   |   | Detected local codeset to be: UTF-8
2010-04-28 09:21:24.105235|INFO    |              |   | Logging started, clientlib version: 3.0.0-beta20 [Build: 10723]
2010-04-28 09:21:24.107432|DEBUG   |              |   | client/clientlib/sound/capturemanager.cpp:26
./ts3client_runscript.sh: line 9:  7921 Illegal instruction     ./ts3client_linux_x86 $@

```

---

### Post by Jon Monreal on 2010-04-28
And you're using the latest version from the Teamspeak site?

Even if you are, you might try downloading again to make sure you have a good copy.

---

### Post by Existance0 on 2010-04-28
Yup, latest version and I redownloaded it same issue.

---

### Post by Jon Monreal on 2010-04-28
> **Existance0 said:**
> Yup, latest version and I redownloaded it same issue.

Could you post the output of the following?
```
cat /proc/cpuinfo
```

Thanks.

---

### Post by JimTaverna on 2010-04-28
Color me confused. You said you dl'd the ".run package" and extracted it to a folder. That's the client version. Only the server is comp'd.

The client (blahblahblah.run) is a single file. All you need to do is make it executable.

Try this:

chmod +x TeamSpeak3-Client-linux_x86-3.0.0-beta20.run
./TeamSpeak3-Client-linux_x86-3.0.0-beta20.run

If you ever need to install the server, read [this]("http://tinyurl.com/teamspeak3serverinstall")

Make the proper adjustemt(s) to the file (ie amd to intel and/or version). He's installing it to a 64bit AMD machine. The procedure is still the same.

---

### Post by Jon Monreal on 2010-04-28
@[JimTaverna]("http://ubuntuforums.org/member.php?u=1061115"): The  client version also extracts to a folder. He's already made it  executable (as he followed [these  instructions]("https://help.ubuntu.com/community/InstallingRunPackage")), and running it results in it being extracted to a  folder.

Running the ts3client_runscript.sh file executes the program.

cat /proc/cpuinfo will tell us if his CPU supports SSE (which is  required by the client).

Screenshot attached (running the x86 client).

---

### Post by JimTaverna on 2010-04-28
Tis true. I stand corrected. Never went past the license screen. Silly me...and pretty stupid](*,). 

All that crap just to extract the data? Would have been better off making it a tar ball like the server. Whoever devised that scheme must have worked for Symantec. The server install must be a hoot.

In any case, my apologies. Hope it works out.

BTW, oak or maple paneling?

---

### Post by Jon Monreal on 2010-04-28
> **JimTaverna said:**
> Tis true. I stand corrected. Never went past the license screen. Silly me...and pretty stupid](*,). 

Don't be so hard on yourself, because:

> All that crap just to extract the data? Would have been better off  making it a tar ball like the server. Whoever devised that scheme must  have worked for Symantec. The server install must be a hoot.

Really. They might as well .zip or .tar it and be done with it. I can understand how on Windows it can make more sense for some users to have a self-extracting .exe, but this needlessly complicates. It would make more sense if they wanted the folder to be in a certain location, but it just dumps it there in the same directory as the .run file.

> BTW, oak or maple paneling?

The wallpaper is from [here]("http://oliuss.deviantart.com/art/Wood-Wallpaper-Pack-113842778"). I find it to be more conducive to working and less distracting than other backgrounds (even just plain colours) because it blends in.

---

### Post by JimTaverna on 2010-04-28
Thanks for the kind words. Still, it was a stupid move, though not necessarily without some semblance of reason. The screen displays something to the effect of "Welcome to the Blah Blah Installer".

Ooops! Saw "Installer" and two words immediately came to mind: Screw That! Didn't care to see 692 entries reminding I just installed a load of junk onto my system. In any case, lesson learned.

As for the wallpaper, I actually like it. Has that homey feel. Something about the brown color that just works in this case. I can't stand ostentatious background crap posing as art, particularly outdoor scenes with every beast in the animal kingdom strolling around like they're at a church picnic. Might work for a Wii with optional 12 gauge Beretta Super 90, but I prefer a little less wild west when I'm online. 

Frankly, the closest I get to garish is the medium grey HP wallpaper I have, with a few very understated white swirls to break the monotony, that came with my mini.

Color me dull.

---

### Post by Existance0 on 2010-04-29
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 5
model name	: Pentium II (Deschutes)
stepping	: 2
cpu MHz		: 397.974
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr up
bogomips	: 795.94
clflush size	: 32

```

---

### Post by Jon Monreal on 2010-04-29
You have a Pentium II processor which does not support the SSE instruction set. The Teamspeak 3 client requires SSE support and will not run unless your CPU supports it (this applies in both Windows and Linux).

Your best bet would be to use an older Teamspeak 2.

---

### Post by Existance0 on 2010-04-30
thank you

---

### Post by Jon Monreal on 2010-04-30
No problem. They really should make it more clear that a Pentium II, (original) Athlon or older won't work.

Could you mark this thread as solved (right above the first post on the page, go to Tread Tools>Mark as Solved)?

Thanks.

---

### Post by feedmebits on 2010-05-06
Awesome thread, this worked for me too :)

---

### Post by Dunlop on 2010-05-08
great advice. thanks for bringing up the question.

now, if i can get DDO going through Wine, ill be set.

---

### Post by itkeepsrepeating on 2010-06-07
I'm having trouble runnin ts3 on my lucid laptop. It seems to install fine, using the instructions mentioned, but when I go to launch it, it gives me:

```
/usr/lib/teamspeak-client/teamspeak.real: symbol lookup error: /usr/lib/teamspeak-client/teamspeak.real: undefined symbol: initPAnsiStrings
```

Should I try using an older version, or the windows version via WINE? 

BTW, I did the cat /proc/whatever and sse is in there... 

Thx in advance...

EDIT/UPDATE: Googling around a bit more yields that this error, produced by a crummy install of ts2 on other distros, means that certain libs were copied to the wrong place. However, they all say to put the libs in /usr/lib, which is where my ts3 is already. Problem is, the place to copy from [on the other distros] doesn't exist, so nothing to copy.

---

### Post by roh8880 on 2010-06-07
Hello everyone!

I tried every step in this section, including the link > [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

But as soon as I click on "Run in Terminal" the terminal pops up for just a split second and disappears. I waited a whole hour and nothing else showed up, I looked at the processes running with the system monitor, and it's not showing there either.

I have a AMD Athlon 64x2 Dual Core Processor, so I think it's sufficient enough. Please Help!

---

### Post by Jon Monreal on 2010-06-10
> **roh8880 said:**
> Hello everyone!

I tried every step in this section, including the link 

But as soon as I click on "Run in Terminal" the terminal pops up for just a split second and disappears. I waited a whole hour and nothing else showed up, I looked at the processes running with the system monitor, and it's not showing there either.

Have you tried the exact instructions above? That is, double-click on  the file "ts3client_runscript.sh" in the folder and select "Run"? The file you download merely unpacks a folder, and therefore the terminal may disappear. You need to run the file in the folder as stated above in order to use Teamspeak.

@itkeepsrepeating: I don't believe you're looking at the same error. The only instance of that error that [I can seem to find by Googling]("http://www.google.com/#hl=en&source=hp&q=%22teamspeak.real%22+%22undefined+symbol%22&aq=f&aqi=&aql=&oq=&gs_rfai=Ca5FHN0YRTJCSPKTuMvy-uNgKAAAAqgQFT9CgNQs&fp=17230b2bfa351c5c") is in this thread. Perhaps you should try downloading and installing again. Also, I will check it later to make sure it isn't a bad build or something.

---

### Post by Zenmij on 2010-08-27
I'm getting a problem after the licence, I type YES - and it says :

NO LOG FILE:

---

