---
title: "Linksys WUSB600N working in hardy and ibex"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by mizunoX on 2008-11-05
I've noticed a few posts from people frustrated with the WUSB600N and the lack of support for it in Ubuntu/Linux so I thought I'd set the record straight for those searching the forums for answers.

The Linksys WUSB600N doesn't work in Ubuntu out of the box (current as of the release of Ibex)
Also it does not play nice with ndiswrapper (frequent disconnects, no 5Ghz support, no WPA2 support)

I was able to get it working with 5ghz and WPA2 by following steps that I found here:
[https://answers.launchpad.net/ubuntu/+question/45440]("Posting on external website")
Credit goes to the original author.

I've downloaded and modified the driver source for your convenience.  

Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar]("http://rapidshare.com/files/160951015/WUSB600N.tar")
Step 2 - Extract WUSB600N.tar to a folder
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder
Step 4 - type "sudo make" without quotes
Step 5 - Copy the file:
[LIST]
[*]sudo mkdir /etc/Wireless
[*]sudo mkdir /etc/Wireless/RT2870STA
[*]sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
[/LIST]
Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.

The wireless card should now be working.

---

### Post by tsali on 2008-11-14
Ok, I erased the Intrepid install and did a clean install of the most recent Hardy tonight.

I am finding that your instructions above are not working.

Here is the error meesages from terminal:

```
chuck@roast-Ubuntu:~/WUSB600N$ sudo make
make -C tools
make[1]: Entering directory `/home/chuck/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function &#8216;main&#8217;:
bin2h.c:34: error: &#8216;FILE&#8217; undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: &#8216;infile&#8217; undeclared (first use in this function)
bin2h.c:34: error: &#8216;outfile&#8217; undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
bin2h.c:49: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:54: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:57: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
bin2h.c:69: error: expected expression before &#8216;)&#8217; token
bin2h.c:71: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:76: error: expected expression before &#8216;)&#8217; token
bin2h.c:78: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:146: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
bin2h.c:155: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/chuck/WUSB600N/tools'
make: *** [build_tools] Error 2
```

I created directories and copied "RT2870STA.dat" as indicated.

I continued despite the errors and was told that there was "no such file" when I tried to enter "sudo insmod rt2870sta.ko"

Any idea what is going wrong?

---

### Post by rvc on 2008-11-16
This worked as advertised!!!  I now have wireless connection with WUSB600N card.
I am new to Linux have been reading the forums trying to figure out how to do this.
Many thanks
RVC
Linux 8.04

---

### Post by mizunoX on 2008-11-19
> **tsali said:**
> Ok, I erased the Intrepid install and did a clean install of the most recent Hardy tonight.

I am finding that your instructions above are not working.

Here is the error meesages from terminal:

```
chuck@roast-Ubuntu:~/WUSB600N$ sudo make
make -C tools
make[1]: Entering directory `/home/chuck/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function ‘main’:
bin2h.c:34: error: ‘FILE’ undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: ‘infile’ undeclared (first use in this function)
bin2h.c:34: error: ‘outfile’ undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function ‘memset’
bin2h.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:54: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:57: warning: incompatible implicit declaration of built-in function ‘strcat’
bin2h.c:69: error: expected expression before ‘)’ token
bin2h.c:71: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:76: error: expected expression before ‘)’ token
bin2h.c:78: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:146: warning: incompatible implicit declaration of built-in function ‘sprintf’
bin2h.c:155: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/chuck/WUSB600N/tools'
make: *** [build_tools] Error 2
```

I created directories and copied "RT2870STA.dat" as indicated.

I continued despite the errors and was told that there was "no such file" when I tried to enter "sudo insmod rt2870sta.ko"

Any idea what is going wrong?


I see some "no such file" errors in there so you must be missing something that I obviously have.

I think stdio.h is supposed to be here: /usr/include (I'm at work right now so I can't check)

If it's not there then install the build-essential package.
I believe it should be on your Ubuntu installation CD.  
Try:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential


...let me know.

---

### Post by tsali on 2008-11-20
Worked perfectly after installing build-essential.

How does a fix like this make it into the official distro?

Thanks for your help.

---

### Post by tsali on 2008-11-20
This is really strange. Since disabling ndiswrapper, the entire UI has sped up significantly. Ubuntu actually has become lightning fast on my machine!

Does this make any sense?

---

### Post by rvc on 2008-11-21
I have to re-apply the mod each time I boot up.  Looking around the various resources I think I might need to edit some boot files but I cannot find exact instructions.  Works fine time each time I execute "sudo insmod rt2870sta.ko" from the WUSB600N/os/linux folder.
What am I missing?

Thanks
RVC
8.04

---

### Post by tsali on 2008-11-21
> I have to re-apply the mod each time I boot up. 

I am having the same problem now...

---

### Post by mizunoX on 2008-11-21
> **rvc said:**
> I have to re-apply the mod each time I boot up.  

Yeah same here - keep in mind that I copied someone else's instructions to get this working.

Let's do a bit of research and report back to this thread if you come up with the answer.  I'll do the same.

---

### Post by mizunoX on 2008-11-21
Okay here's what I've found (and anyone with more linux knowledge is free to correct me if there's a better way).

Copy the .ko file to the kernel modules folder:
```
sudo mkdir /lib/modules/<kernel version>/wireless
sudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
```

Edit the modules list
```
sudo gedit /etc/modules
```

Add the following to the bottom:
```
rt2870sta
```

Edit the startup script:
```
sudo gedit /etc/rc.local
```

Add this near the end but before "exit 0"
```
sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko
```


I'm at work so I'm going to have to try this later when I get home.

---

### Post by tsali on 2008-11-22
That seems to have done the trick! It's loading at startup now...

Lest I be accused of freeloading, I really was trying to figure out how to add this rc.local this morning...

I get why we added the line to rc.local, but why did we have to make the wireless directory in /lib/modules/<kernel> and make the changes to "etc/modules" that we did?

Trying to learn...

---

### Post by rvc on 2008-11-24
Working OK for me too.  Thanks!

---

### Post by rmcellig on 2008-11-24
I'm pretty new to working in the terminal and need help with step 3 and 4. How do I do these steps?

---

### Post by impala79 on 2008-11-29
Great thread misunoX! I followed your instructions to install the driver and then to get it to load on startup. I restarted the computer, and dmesg told me the driver was loaded (I should mention I didn't even have the hardware connected yet)

I then went out and picked up WUSB600N from staples, plugged it in, and it worked perfectly. Ibex detected it, asked for permission to start up a Network Protocol program to get wireless going, and then it detected all of the routers in range. 

Now I'm connected very stably at 270 Mb/s. Very cool. 


Rmcellig, to help you wout with steps 3 and 4:

To open your terminal go to Applications -> Accessories -> Terminal

Once there, to navigate to your created directory just type it's path. I had mine sitting on the desktop, so I typed

cd Desktop/WUSB600N

Hit enter and you'll be in that directory. now for step 4. simply type

sudo make

it will ask for your admin password. Type it in, but note that in the terminal when you enter a password, nothing appears in the terminal! It's like you're typing ghost letters or something! so just type in your password and hit enter, and a whole lot of stuff should appear in the terminal window. Wait for this to stop. When it does you'll have the regular terminal command line back.

Now for step 5 just type those three sudo commands and hit enter after each.

For step 6 first type

cd /os/linux

Then type that sudo insmod... command. 

To have the module load at startup, follow the post at the bottom of page 1. I think it'll be easy once you've got a handle on what you hopefully successfully did above!

---

### Post by mizunoX on 2008-11-29
Thanks Impala, and thanks for adding information to the thread.

Just a note since I notice that my update manager is trying to push a new kernel today...  if you do update your kernel you may have to recompile the driver.
I could be mistaken but I think since we compiled based on previous kernel headers when we upgrade to a new kernel the driver will stop working.

Just be prepared.. have the instructions saved offline if you plan to upgrade to the new kernel.

---

### Post by chooser on 2008-11-30
I've followed all of your steps and I run into this.

matt@ubuntu:~$ /home/matt/Documents 
bash: /home/matt/Documents: is a directory 
matt@ubuntu:~$ sudo make 
make: *** No targets specified and no makefile found.  Stop. 
matt@ubuntu:~$  

What am i doing wrong? :confused:

---

### Post by impala79 on 2008-11-30
You simply forgot to type "cd" before your "/home/matt/Documents" command. So assuming you've unzipped the contents of the WUSB600N.tar file to /home/matt/Documents, you'd need to type "cd /home/matt/Documents" into the terminal. 

Also, if you're logged in as "matt" once you open the terminal you should already be in /home/matt, so you'd really only have to type "cd Documents"

If that still doesn't work, double check as to where you've unzipped the tarball. That location is where you need to be! I saved mine to the desktop, and when it unsipped it created a folder called WUSB600N, so i had to type "cd Desktop/WUSB600N" as my very first terminal command.

Good Luck!

---

### Post by impala79 on 2008-11-30
mizunoX, I can confirm that I had to redo this procedure for the new kernel. Ah such is the nature of the beast. My VirtualBox stuff always needs to be re-installed too every time there's a new kernel. 

Anyway, yeah, new kernel, follow the same instructions as before, and you'll all be gold!

---

### Post by chooser on 2008-11-30
[[IMG]http://img237.imageshack.us/img237/5099/whatswronglw0.th.jpg[/IMG]](http://img237.imageshack.us/my.php?image=whatswronglw0.jpg)

What am I doing wrong?

---

### Post by impala79 on 2008-11-30
ah ok, you've yet to unzip your WUSB600N.tar. 

If you want to get linux geeky, you can just type 

tar -xvvf WUSB600.tar

after you've entered the directory of WUSB600.tar, which is what you did with your "cd /home/matt/Documents/adapter" command.

OR you can use the Gnome GUI to do this part of it:
Click on that WUSB600N.tar file and a window will open showing a single folder called WUSB600N. Drag that folder into your /home/matt/Documents/adapter folder. 

Whether you used the terminal or the GUI, you should now have two items in /home/matt/Documents/adapter; the WUSB600N.tar file and the WUSB600N folder. It's the WUSB600N folder that contains all the magic.


Now in your terminal type "cd Documents/adapter/WUSB600N"

Now try your "sudo make" and go from there...

---

### Post by impala79 on 2008-11-30
I'm off to bed. If you still need help I'll be glad to pitch in tomorrow!

---

### Post by chooser on 2008-11-30
I ran into a problem at step 6.

[[IMG]http://img165.imageshack.us/img165/3165/screenshot1zt8.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshot1zt8.png)

Also, I don't get the start up part on the bottom of page 1. Thanks.

---

### Post by impala79 on 2008-11-30
OK I see what you did (or didn't do in this case!). Before you type in the insmod command you need to be in the /os/linux subdirectory of the WUSB600N. So simply type

cd /home/matt/Documents/WUSB600N/os/linux

right before you type

sudo insmod rt2870sta.ko.

So really from start to finish what you'll type (assuming you've already unzipped the original WUSB600N.tar file, which it looks like you did!)

cd /home/matt/Documents/WUSB600N

sudo make

(Enter Password, unless you've already done that)

sudo mkdir /etc/Wireless

sudo mkdir /etc/Wireless/RT2870STA

sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

cd /home/matt/Documents/WUSB600N/os/linux

sudo insmod rt2870sta.ko


Now for the startup part. I imagine you're confused about the <kernel version> portion of the command. Basically depending on your distribution of Linux and how updated it is, you'll have a folder in /lib/modules/ for each kernel available to you. When you boot up your machine, are you given the option as to which version of Ubuntu you want to load? I have a few options, since I have the original kernel that came with Ibex  and the new kernel that my machine added yesterday in the system update. Which ever one you're selecting upon booting is the one we'll work with here. 

To get the actual directory name, open your file browser (Nautilus) and in the address bar type in /lib/modules. You'll notice at least one folder here. Write down the name of the folder with the highest version number, since this is probably the one you've booted into. Now for the instructions on the startup procedure where ever you see <kernel version>, replace that with the name of the folder that you've written down, and remember don't include the <> part!

So that takes care of the first two steps of this procedure.
The last part has you editing two system files. Just copy those sudo gedit ... commands into the terminal one at a time

After you run each a text editor will open the required file for you to edit. Paste the text from the instructions into their respective files and save them and close them.

---

### Post by rvc on 2008-12-02
I wish I had checked the forum before I installed the new kernel!  Wireless connection went down so I figured that I would need to create the new folders with the new kernel name.  Did all that OK but it still did not work.  I then started checking around and saw your info about recompiling the driver.  That was the answer.  All is well again.
Many thanks.

---

### Post by w1ll15 on 2008-12-09
My wusb600n works fine in ubuntu 8.10 . (NOW)!! 

here is what i did :

if you have the install disk for your wusb600n it has a win XP driver on it. ( .dll )

from desktop go to System > Admin > windows  wireless Drivers and install.

now the light should be blinking on the adapter.

It still wouldnt work witth wifi-radar but try going to the connection icon
@ top right corner and

right click  > enable wireless
Left click to veiw wireless networks 
try connecting that way

also make sure your wireless router  is set to a mixed network my wusb600N is being recognized as a G adapter 

But it does work 

I will say though no luck with 

wifi=radar 
ndiswrapper

---

### Post by cyberDrake on 2008-12-15
How can I get the WUSB600N to be seen as a "n" device? I followed the instructions in this thread and get it to working, but :

```

shimmergloom:~/WUSB600N/os/linux$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"souma"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:22:6B:4F:8F:A7
          Bit Rate=48 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=91/100  Signal level:-72 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

any ideas?

---

### Post by 0x4B61726E on 2008-12-18
im using breezy badger and trying to get this to work, i installed the build-essential and when i try 'sudo make' i get this;

[B]karn@nixar:~/Documents/WUSB600N$ sudo make
make -C tools
make[1]: Entering directory `/home/karn/Documents/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/karn/Documents/WUSB600N/tools'
/home/karn/Documents/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/karn/Documents/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.12-9-386/build SUBDIRS=/home/karn/Documents/WUSB600N/ os/linux modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
karn@nixar:~/Documents/WUSB600N$[/B]

i tried to install kernel-source and got 'couldnt find package' error,
i tried "dpkg -S /lib/modules/2.6.12/build", that couldnt be found
i tried "export CC=gcc-3.4". then "make clean", still, same error
and i tried "sudo apt-get install linux-source-$(uname -r)"

Then..i tried "sudo apt-get install linux-headers-$(uname -r)"
that made alot of stuff come up but i think most of it was errors and warnings

its about 2500 lines of errors and whatnot i tried to create a log but it only went back a few hundred lines even after i changed scrolling to 2500 lines it would only let me go back a few hundred, theres alot of things like;

/home/karn/Documents/WUSB600N/include/ap.h:327: error: syntax error before ‘pAd’/home/karn/Documents/WUSB600N/include/ap.h:327: warning: function declaration isn’t a prototype
/home/karn/Documents/WUSB600N/include/chlist.h: In function ‘CreateChList’:
...and
/home/karn/Documents/WUSB600N/include/chlist.h:1025: error: ‘pChRegion’ undeclared (first use in this function)
/home/karn/Documents/WUSB600N/os/linux/../../common/md5.c:110: error: ‘k_opad’ undeclared (first use in this function)
...and
/home/karn/Documents/WUSB600N/os/linux/../../common/md5.c:112: warning: implicit declaration of function ‘memmove’
/home/karn/Documents/WUSB600N/os/linux/../../common/md5.c:124: error: ‘data_len’ undeclared (first use in this function)
and ends with something like....

make[2]: *** [/home/karn/Documents/WUSB600N/os/linux/../../common/md5.o] Error 1
make[1]: *** [_module_/home/karn/Documents/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/scr/linux-headers-2.6.12-9-386'
make: *** [LINUX] Error 2

im not sure what else to do, i have an older laptop (gateway solo 2550) with 430mhz and 98mb ram, so i cant really install hardy or ibex, i dont think,

---

### Post by DJ_Peng on 2009-01-04
> **mizunoX said:**
> Okay here's what I've found (and anyone with more linux knowledge is free to correct me if there's a better way).

Copy the .ko file to the kernel modules folder:
```
sudo mkdir /lib/modules/<kernel version>/wireless
sudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
```Edit the modules list
```
sudo gedit /etc/modules
```Add the following to the bottom:
```
rt2870sta
```Edit the startup script:
```
sudo gedit /etc/rc.local
```Add this near the end but before "exit 0"
```
sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko
```I'm at work so I'm going to have to try this later when I get home.
You rock, mizunoX. We had a router die on us the other day and we decided it was time to move up to wireless 'net connections. The other comps on our net run WinXP but your thread helped me ne ready for my USB adapter when it arrived from the store.

I'm applying the edit quoted above, but I have a query. WIll I have to manually make these edits each time I upgrade my kernel? I know I have an upgrade to Intrepid in store once I get a few other things taken care of in Hardy.

Either way I owe yo a beer. Or two.

---

### Post by zhukov8885 on 2009-01-14
hey im new to this and im trying to get this to work but i get to:

            "open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes"

when i try this i get the message: insmod: error inserting 'rt2870sta.ko': -1 Unknown symbol in module
      
what am i doing wrong? ive been trying to get this to work because i really want to switch to linux but so far it has just been a huge pain in my a$$. any help would be greatly appreciated.

---

### Post by smckenzie on 2009-01-16
I got as far as this, and then when i rebooted i still had to add the script "insmod"....etc, it isn't detecting it straight away.
> Add this near the end but before "exit 0"
Code:

sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko



---

### Post by DFord425 on 2009-01-19
> **0x4B61726E said:**
> im using breezy badger and trying to get this to work, i installed the build-essential and when i try 'sudo make' i get this;

[B]karn@nixar:~/Documents/WUSB600N$ sudo make
make -C tools
make[1]: Entering directory `/home/karn/Documents/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/karn/Documents/WUSB600N/tools'
/home/karn/Documents/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/karn/Documents/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.12-9-386/build SUBDIRS=/home/karn/Documents/WUSB600N/ os/linux modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
karn@nixar:~/Documents/WUSB600N$[/B]

Does anyone know how to solve this problem?

---

### Post by DFord425 on 2009-01-20
Anyone have any ideas on how to solve the above problem?

---

### Post by DJ_Peng on 2009-01-20
Is Breezy supported any longer? I ask only because I'm not sure there's a solution due to dependency issues, but I welcome anyone to point out my error.

---

### Post by DFord425 on 2009-01-20
Im sorry, i should have specified, i am using 8.10 but im getting the same error as the other guy using breezy

---

### Post by DFord425 on 2009-01-21
Bump, any ideas?

---

### Post by JimXugle on 2009-01-22
It seems like you need the kernel source or headers or something.

---

### Post by HighCommander540 on 2009-01-22
Does anyone know if there is something extra you would have to do to use the technique on the server edition?

---

### Post by akisawana on 2009-02-03
I...don't have the .ko file in /os/linux
Command line spat an error at me -that file doesn't exist.
Checked the folder, the tarball, and re-downloaded it.
Where does it come from?

---

### Post by mizunoX on 2009-02-03
> **akisawana said:**
> I...don't have the .ko file in /os/linux
Command line spat an error at me -that file doesn't exist.
Checked the folder, the tarball, and re-downloaded it.
Where does it come from?

The rt2870sta.ko files is created when you compile (or "sudo make").

What was that output when you did did sudo make?

---

### Post by akisawana on 2009-02-03
> **mizunoX said:**
> The rt2870sta.ko files is created when you compile (or "sudo make").

What was that output when you did did sudo make?

Well, I called my brother after he got out of class (he's sixteen) and he told me "idiot, you have to compile it. You can't just drag and drop it even if it lets you."
So I've got it now! Thank you for your tutorial, if you *actually* follow directions instead of logging onto root to drag-and-drop, it works perfectly!

---

### Post by Chiatroll on 2009-02-14
Following the instructions I understood I get it working.. but only until the next reboot and it doesn't work like it is n it just works like a regular adapter. I know because my router puts off 2 SSIDs and it sees the g one but not the n.

---

### Post by Leafworks on 2009-02-18
> **mizunoX said:**
> 
Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar]("http://rapidshare.com/files/160951015/WUSB600N.tar")
Step 2 - Extract WUSB600N.tar to a folder
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder
Step 4 - type "sudo make" without quotes
Step 5 - Copy the file:
[LIST]
[*]sudo mkdir /etc/Wireless
[*]sudo mkdir /etc/Wireless/RT2870STA
[*]sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
[/LIST]
Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.

The wireless card should now be working.

Mizuno, the only problem I am having is with step #6. The error I am getting specifically is that the file rt2870sta.ko doesn't exist. I have dowloaded and unzipped the .tar file, and followed the rest of the instructions to the letter, though I have been scratching my head trying to find the .ko file. 

I'm new to ubuntu, but I am fairly adept at following command line instructions. I need help with this one though. Please? :)

---

### Post by DJ_Peng on 2009-02-19
I keep being thankful for this thread. I grabbed a kernel upgrade the other day and luckily I had this thread saved to my hard drive. I needed it to remember how to get the new kernel set up to use my wireless again so I could get back online. I may have missed it, but does anyone know of a bug to get the driver updated automatically when a new kernel comes down the pike? It's a real pain having to go through this process every upgrade.

---

### Post by Leafworks on 2009-02-19
This needs to be done with every Kernel upgrade? Cheese and crackers, I haven't even been able to get online with it once... lol, I'm gonna need to do this again as soon as I finish. Hopefully, like you said, someone has come up with a fix for that.

---

### Post by DJ_Peng on 2009-02-19
I'm afraid to say this, but yes, partly. When I grabbed the 2.6.27.12 kernel I couldn't use my USB wireless until I copied the files into the new kernel folder and edited the /etc/rc.local file. It's a couple of steps and you only have to do them when you get an updated kernel, but people like me who grab intrepid-proposed will have to do them more often.

My video drivers get updated automatically, and it would help a lot to get my wireless drivers/settings updated as well.

---

### Post by b3nw on 2009-03-04
interesting enough, I couldn't get this to load on boot until I removed the line from /etc/modules.

It seems when it auto loads from /etc/modules, it doesn't load properly for whatever reason, and then when /etc/rc.local runs, the insmod fails as its already loaded (brokenly).

Also, creating a ln -s for the module, will allow you to just do sudo make each time there is a kernel update and everything else will work.

hope that helps.

---

### Post by Susan Potocki on 2009-03-24
ARRRGGGGHHHH!!!!!

I'm running a clean install of Intrepid.  I originally downloaded the drivers from the ralink site and modified them myself.  This resulted in the problem I'll describe below.  Then I tries the driver code in the WUSB600N.tar file in this thread.  Funny enough, the code is identical except for the comments I added myself.  And I get the same end result.  Regardless, during the compiles I get the following warnings:

> /[...]/WUSB600N/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/[...]/WUSB600N/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used

...

 MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'

I don't know if these have anything to do with the problem I'm having, but I just thought I should mention them.  Other than these warnings, the compile goes smoothly.  Then I copied the .dat file as instructed and inserted the module.  Again, no problems.  The WUSB600N lights up, I can see it in iwconfig and ifconfig.  It sees my access point with an iwlist scan.  It associates to my access point (I think), and everything looks hunky dory (although the signal to noise ratio data in iwconfig seems a little wacky).

HOWEVER...

When I try to ping my AP or send any other data (dhcp requests etc) I get "Destination Host Unreachable", and upon checking my kernel messages I see these messages:

> $dmesg
[ 1515.414787] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1515.414878] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1515.414943] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1515.415009] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1515.423716] 1. Phy Mode = 5
[ 1515.423739] 2. Phy Mode = 5
[ 1515.505590] RTMPSetPhyMode: channel is out of range, use first channel=1

And then a whole lot of this repeated over and over and over:

> $dmesg
[ 1780.844172] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 964
[ 1781.212600] DRS: unkown mode,default use 11N 2S AP 
[ 1781.212633] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[ 1790.738767] DRS: unkown mode,default use 11N 2S AP 
[ 1790.738800] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)

What is going on here?  What am I doing wrong? I followed the instructions in this thread EXACTLY.

I have been trying to get a working wireless solution here for MONTHS, but the selection here in rural Canada is limited to what's at Walmart (and with all the failed trials, I'm sure as heck not doing the mail-order thing).

---

### Post by Susan Potocki on 2009-03-24
> **DFord425 said:**
> Does anyone know how to solve this problem?

I'm surprised nobody's helped you with this.  You're missing the kernel headers.

That's generally the problem whenever you see a warning like this:
> make: *** /lib/modules/[...]/build: No such file or directory. Stop.

If you're running a generic kernel, try:
```
sudo apt-get install linux-headers-generic
```

If you're running a more specific kernel, you'll have to install the headers specifically for that kernel.  This trick usually works:
```
sudo apt-get install linux-headers-$(uname -r)
```

Personally, I think the kernel headers should be a dependency of build-essential, but that's just me.

---

### Post by JMannering129 on 2009-04-12
> **mizunoX said:**
> I see some "no such file" errors in there so you must be missing something that I obviously have.

I think stdio.h is supposed to be here: /usr/include (I'm at work right now so I can't check)

If it's not there then install the build-essential package.
I believe it should be on your Ubuntu installation CD.  
Try:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential


...let me know.

im getting the same problem that tsali had and i dont know what to do.

---

### Post by JMannering129 on 2009-04-12
> **impala79 said:**
> Great thread misunoX! I followed your instructions to install the driver and then to get it to load on startup. I restarted the computer, and dmesg told me the driver was loaded (I should mention I didn't even have the hardware connected yet)

I then went out and picked up WUSB600N from staples, plugged it in, and it worked perfectly. Ibex detected it, asked for permission to start up a Network Protocol program to get wireless going, and then it detected all of the routers in range. 

Now I'm connected very stably at 270 Mb/s. Very cool. 


Rmcellig, to help you wout with steps 3 and 4:

To open your terminal go to Applications -> Accessories -> Terminal

Once there, to navigate to your created directory just type it's path. I had mine sitting on the desktop, so I typed

cd Desktop/WUSB600N

Hit enter and you'll be in that directory. now for step 4. simply type

sudo make

it will ask for your admin password. Type it in, but note that in the terminal when you enter a password, nothing appears in the terminal! It's like you're typing ghost letters or something! so just type in your password and hit enter, and a whole lot of stuff should appear in the terminal window. Wait for this to stop. When it does you'll have the regular terminal command line back.

Now for step 5 just type those three sudo commands and hit enter after each.

For step 6 first type

cd /os/linux

Then type that sudo insmod... command. 

To have the module load at startup, follow the post at the bottom of page 1. I think it'll be easy once you've got a handle on what you hopefully successfully did above!

i did just like you said and i got an error stating "insmod:  error inserting 'rt2870sta.ko': -1 file exists " what should i do now?

---

### Post by DJ_Peng on 2009-04-13
It looks like the issue is finally resolved in 9.04 (Jaunty). I've gotten a couple of kernel updates after the initial dist-upgrade and I haven't had to manually update the WiFi information since I left 8.10 (Intrepid).

---

### Post by subtorn on 2009-04-13
Hey all, new user here (running hardy for 3 days now) and just wanted to drop some mad props to mizunoX for this & say thanks to everybody else for posting.  I learn something new every time I visit the forums.

I'm sitting here looking at the green light finally blinking on my adapter at long last :guitar:

Thanks for making this easy enough for a clueless noob such as myself to figure out.

I've found that dragging the extracted folder over to the terminal and dropping it (careful to remove the ' the front and back of the line as well as the space) helps me after typing cd .  Not sure if this is a standard practice for everybody or not, just found it useful earlier today and like how much time it saves.

Off now to see if this thing can be configured to monitor as well since my ar5007eg built-in wireless card is being such a spaz and won't switch over to monitor mode...8-)

---

### Post by Dirigo on 2009-04-26
I used this thread to get my WUSB600N working with great success, but it only connects @ 54 Mb/s under Ubuntu (both 8.10 and 9.04).  I'm running a dual boot w/ Vista Ultimate, and in Windows it connects @ 270 Mb/s.  How can I get this kind of connection speed w/ 9.04?  Thanks for any help.

---

### Post by mizunoX on 2009-04-28
> **Dirigo said:**
> I used this thread to get my WUSB600N working with great success, but it only connects @ 54 Mb/s under Ubuntu (both 8.10 and 9.04).  I'm running a dual boot w/ Vista Ultimate, and in Windows it connects @ 270 Mb/s.  How can I get this kind of connection speed w/ 9.04?  Thanks for any help.

It looks like 9.04 has included support for the rt2870 chipset "out of the box" but it's somehow limited or broken.
I'm having the same issue.  I did a fresh 9.04 install and the device is working, but will only connect at 54Mb/s.

I'm going to mess with it tonight and see what I can do.

---

### Post by zurgprot on 2009-04-28
I was just stumbling around trying to get my wusb600n working with n mode.  9.04 detects it and it works with g mode only.

So I went to the Ralink site [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") and found that they have source code for new drivers that was released on April 24.

I downloaded it and did a make, make install in the unzipped directory.  Plugged in my wusb600n and boom, it detected my wireless n network.

NOTE: the wusb600n is the rt2870 chipset.

Hope this helps.

---

### Post by gyzzofytal on 2009-04-29
Hi everybody,
zurgprot, can you explain how do you install drivers released on April 24?

Didn't you use the sentence "insmod"?

I have problems to install new ralink driver in 9.04  Do I have to uninstall previous version of the driver?

---

### Post by mizunoX on 2009-05-03
> **zurgprot said:**
> I was just stumbling around trying to get my wusb600n working with n mode.  9.04 detects it and it works with g mode only.

So I went to the Ralink site [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") and found that they have source code for new drivers that was released on April 24.

I downloaded it and did a make, make install in the unzipped directory.  Plugged in my wusb600n and boom, it detected my wireless n network.

NOTE: the wusb600n is the rt2870 chipset.

Hope this helps.

I can confirm that this is working for me too.  Before installing I connected at 54Mb/s and my LAN transfer was going 700KB/s, after installing and rebooting I am connected at 117Mb/s and transferring the same file across the LAN at 1500KB/s.

I did as he said.  Downloaded the tar.gz file.
Extracted it.  
Entered the folder and did 'sudo make', 'sudo make install', then rebooted.
EDIT - just switched my router to 5Ghz, now connecting at 300Mb/s and transferring that file at 5000KB/s.  This is important because if it wasn't working in N mode I wouldnt be able to connect to a 5Ghz broadcasting router.

---

### Post by diy on 2009-05-07
> **mizunoX said:**
> Okay here's what I've found (and anyone with more linux knowledge is free to correct me if there's a better way).

Copy the .ko file to the kernel modules folder:
```
sudo mkdir /lib/modules/<kernel version>/wireless
sudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
```Edit the modules list
```
sudo gedit /etc/modules
```Add the following to the bottom:
```
rt2870sta
```Edit the startup script:
```
sudo gedit /etc/rc.local
```Add this near the end but before "exit 0"
```
sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko
```
I'm at work so I'm going to have to try this later when I get home.

Hello All, I am new to the forum and Linux. I am running Ubuntu with the wusb600n adapter and I got it working with the instructions provided, but when I reboot I have to do it over and I don't quite understand the instructions to make it permanent. Can someone go into a little more detail. I tried copying and pasting all the codes above in the terminal but i does not seem to be working.

Thanks in advance

---

### Post by mizunoX on 2009-05-11
> **diy said:**
> Hello All, I am new to the forum and Linux. I am running Ubuntu with the wusb600n adapter and I got it working with the instructions provided, but when I reboot I have to do it over and I don't quite understand the instructions to make it permanent. Can someone go into a little more detail. I tried copying and pasting all the codes above in the terminal but i does not seem to be working.

Thanks in advance


Check post #10 on page 1 if you followed the instructions from post #1.

---

### Post by Gemu on 2009-06-14
I did step 1 through 6 at the front of this post and got the light to comee on on my usb router but its still not working. Is there something else needed for it to work with 8.10 Ubuntu? There is no kind of graphical interface that shows available wi-fi connections. I recently had an ethernet wired connection.

---

### Post by Gemu on 2009-06-14
I got it working on 8.10 intrepid. I misunderstood on the <kernel version> thing at the bottom of page one and literaly created a folder named kernel version to put my new wireless folder in. #-o 

Now I know that I should end up with-  

 lib/modules/2.6.27-11-generic/Wireless/rt2870sta.ko 


and I have to do it all over again if I update the kernel. Thanks for the instructions.

---

### Post by haakon on 2009-07-07
Trying to get my new WUSB600N to work in Jaunty. It works fine on unencrypted nets, but I can't get wpa_supplicant to associate when I turn on wpa or wpa2 on the router. It basically loops with this output:

```
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:23:69:xx:xx:xx (SSID='myssid' freq=2417 MHz)
Authentication with 00:23:69:xx:xx:xx timed out.
```

I have a new N router set up to be N only which I have tested against, but I also have an older G router which it can't associate to either.

I have installed the latest driver from ralink, made sure I have the latest firmware in /lib/firmware, even tried editing /etc/Wireless/RT2870STA/RT2870STA.dat with my connection data, but nothing helps. I can't find others with these kinds of problems, so what am I doing wrong?

Thanks!

---

### Post by tsali on 2009-07-11
I am having the same problem you are.

New ralink drivers (5/21/2009) appear to be driving the adapter but it will not authenticate on WPA!

Anyone have any ideas?

At the very least, can someone tell me how to restore everything back to its original state? A slower connection is better than no connection.

---

### Post by PePeLuKaS on 2009-07-24
Hello everybody!

First of all, thank you for this thread, it's very helpfull.


I use this guide and my WUSB600N works fine, but i have one problem.

i did things in post 1 and 10 (page 1) but for some reason when i restart my wireless adapter does not work, the led is active but in the network connection applet there's no a "wireless connections" option, so i need to do a "sudo rmmod..." and then load again the module with a "sudo insmod". only this way works after reboot.

I repeat. i did things in post 10 on page 1, module loads but dont work fine.

I'm on Ubuntu hardy with a "2.6.24-23-generic" kernel.

Can anyone tell me what i am doing wrong?

thank you very much and excuse me about my bad english.

---

### Post by furiousdog on 2009-07-26
This is a very helpful thread, thanks!

> **tsali said:**
> I am having the same problem you are.

New ralink drivers (5/21/2009) appear to be driving the adapter but it will not authenticate on WPA!

Anyone have any ideas?

I had these problems getting my WUSB600N to work but then I re-read the first post and noticed the link to [https://answers.launchpad.net/ubuntu/+question/45440](https://answers.launchpad.net/ubuntu/+question/45440)

A couple of the source files need to be edited to enable WPA authentication. The sources have changed a bit since that original post so I will outline what I did.

1. Download the drivers from the [Ralink site](http://www.ralinktech.com/ralink/Home/Support/Linux.html), the RT2870USB (at the time of writing the latest are 5/21/2009 2.1.2.0)

2. Extract the files. Then with your favorite editor open up the os/linux/config.mk file and look for the two lines (should be around the top)
    HAS_WPA_SUPPLICANT=n
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

3. Change them both to 
    HAS_WPA_SUPPLICANT=y
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

4. Then,
    $ sudo make
    $ sudo make install

Then after a restart I was on 270Mb/s. I did notice that the connection wasn't stable and the signal went down a bit but there could be other issues coming into play (I don't think I've set up the router correctly)

> **tsali said:**
> At the very least, can someone tell me how to restore everything back to its original state? A slower connection is better than no connection.

Sure, this seemed to work for me,
    $ sudo make uninstall

then restart.

Hope this helps.

btw I am running 9.04 Jaunty

---

### Post by UltraAnders on 2009-08-02
> **mizunoX said:**
> I can confirm that this is working for me too.  Before installing I connected at 54Mb/s and my LAN transfer was going 700KB/s, after installing and rebooting I am connected at 117Mb/s and transferring the same file across the LAN at 1500KB/s.

I did as he said.  Downloaded the tar.gz file.
Extracted it.  
Entered the folder and did 'sudo make', 'sudo make install', then rebooted.
EDIT - just switched my router to 5Ghz, now connecting at 300Mb/s and transferring that file at 5000KB/s.  This is important because if it wasn't working in N mode I wouldnt be able to connect to a 5Ghz broadcasting router.Nice one :guitar: Was only able to connect to 2.4 GHz networks, but this worked a treat for me.

I solved the issue of no "rt2870sta.ko" file in the /os/linux directory by moving the extracted files to a directory path that contained no spaces. I also moved the file to within my home directory, but I'm pretty sure it's the spaces that caused the issue. When I ran "sudo make install" for the first time I noticed the directory name in an error was truncated at the first space. Seems like a bit of a silly thing to fall over on!

---

### Post by studeski on 2009-08-07
> **furiousdog said:**
> This is a very helpful thread, thanks!



I had these problems getting my WUSB600N to work but then I re-read the first post and noticed the link to [https://answers.launchpad.net/ubuntu/+question/45440](https://answers.launchpad.net/ubuntu/+question/45440)

A couple of the source files need to be edited to enable WPA authentication. The sources have changed a bit since that original post so I will outline what I did.

1. Download the drivers from the [Ralink site]("http://www.ralinktech.com/ralink/Home/Support/Linux.html"), the RT2870USB (at the time of writing the latest are 5/21/2009 2.1.2.0)

2. Extract the files. Then with your favorite editor open up the os/linux/config.mk file and look for the two lines (should be around the top)
    HAS_WPA_SUPPLICANT=n
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

3. Change them both to 
    HAS_WPA_SUPPLICANT=y
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

4. Then,
    $ sudo make
    $ sudo make install

Then after a restart I was on 270Mb/s. I did notice that the connection wasn't stable and the signal went down a bit but there could be other issues coming into play (I don't think I've set up the router correctly)



Sure, this seemed to work for me,
    $ sudo make uninstall

then restart.

Hope this helps.

btw I am running 9.04 Jaunty

I'm running jaunty jackalope and have done everything mentioned here and mine still doesn't work. What information do you need to help me?

Thanks,

---

### Post by deankovell on 2009-08-08
I'm also running jaunty  and can't get iwconfig or ifconfig to show the device. Some of the posts said that jaunty had native support for the rt2780, but I'm not seeing any thing like that.  I am runnung the 64 bit ubuntu studio rt kernel, does that make a difference?

---

### Post by deankovell on 2009-08-10
there are issues with rt kernels. I found this post here:
[http://ubuntuforums.org/showthread.php?t=766850&page=6](http://ubuntuforums.org/showthread.php?t=766850&page=6)

> [SIZE=2]hello,
I come back with a very good new! Problem solved!! for months I've been fighting with it but now it's ok!

So, in fact with "-rt" kernels the problem seems to come regularly, and I found the post of someone with the same warning during the installation of his webcam.
The only thing I had to do is: 
to edit "2008_0925_RT2870_Linux_STA_v1.4.0.0./include/rtmp.h" and 
to change "struct semaphore" into "struct compat_semaphore" on the lines 2716, 2717, 2718 and 2720.[/SIZE]
                                                                                  
edit: I jumped the gun a little bit. I tried the modified driver provided by the op in 64studio (older kernel, but still w/ an rt patch) and it worked. I tried the newest version of the driver in jaunty without editing a .h file, and didn't get the error about rt semaphores. good.  it compiled and loaded the driver, but it won't scan anything, and the blue light just stays on instead of flashing. also the file where you might have to add your device id is in a diff. location. " /os/linux/usb_main_dev.c". wusb600n was listed but the numbers were different than what lsusb showed me, so I changed it to match. Does anybody have a clue why the device isn't scanning, and what info do I need to provide to diagnose the problem? if it's the device id thing, do I have to uninstall the driver before I edit the text back to what it originally was?


 [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=5947223")                [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=5947223")

---

### Post by NeedSomeHelp on 2009-08-11
Hi ,

I tried to installled my WUSB600N USB wireless card on my ubuntu8.04 32 bit Desktop. I followed the instruction on thyis tread. But the LED light on USB Card didn't blink at all . I did some diagnostic .
1.#lsusb
Bus 005 Device 002:ID 1737:0079
.......................
.......................
Seems computer recognized the USB Stick .

2.#dmesg:
[241.971014]rtusb init --->
[241.971438]usbcore:registered new interface driver rt2870
.....................
.....................
Seems the Ralink rt2870 driver loaded successfully.

3.#iwconfig
lo no wireless extensions
eth0 no wireless extensions

 I don't know what  to check now and what's wrong with my installation.

Any help would be greatly appreciated.


  	
	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7765648")

---

### Post by thecow on 2009-08-23
I am having the same problem with the new version of the driver v2.2.0.0

I have installed it and I see the blue light on the USB stick now.  I had to alter the c file mentioned above and put in 1737:0079 instead of 0071.  Not sure if the new sticks have a different hardware revision or what the issue is but that allowed the light to finally come on.

Now however I see no way to scan for networks.  Unfortunately the Network Manager that comes with Ubuntu has no ability to change devices if you have two so I downloaded wicd.  When I try to tell wicd to use ra0 it tells me it cannot scan for networks.

I tried to edit the .dat file that comes with the driver and input the networks name, WPA key etc..  However that seems to have done nothing except now in iwconfig it lists the name I want it to connect to in ESSID

Here is ifconfig
brian@brian:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:76:58:c1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:15:00:10:bc:ef  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe10:bcef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4065 errors:5 dropped:34 overruns:0 frame:0
          TX packets:2920 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2640248 (2.6 MB)  TX bytes:559793 (559.7 KB)
          Interrupt:17 Base address:0x6000 Memory:fe9ff000-fe9fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21656 (21.6 KB)  TX bytes:21656 (21.6 KB)

ra0       Link encap:Ethernet  HWaddr 00:25:9c:03:79:58  
          inet6 addr: fe80::225:9cff:fe03:7958/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:18392 (18.3 KB)







Here is iwconfig
brian@brian:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Laura's Network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:59:3A:D7   
          Bit Rate:24 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-57 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:5  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:29   Missed beacon:10

pan0      no wireless extensions.

ra0       Ralink STA  ESSID:"Laura's Network"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:




Here is lsusb
brian@brian:~$ lsusb
Bus 001 Device 002: ID 1737:0079 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub





Thank you for your time

---

### Post by thecow on 2009-08-23
Seems that Linksys has been putting out a version 2 of the WUSB600N.  Us lucky chaps are there out of luck it seems

---

### Post by mrjogo on 2009-09-04
Using furiousdog's method, plus doing the insmod step, I got my version 2 to light up its LED, and be detected by ifconfig and iwconfig (as interface ra0). Unfortunately, now I can't use iwconfig to change the essid from what appears to be the default (ESSID:"11n-AP" Nickname:"RT2870STA"). I should be able to just do "sudo iwconfig ra0 essid "my_essid"" to change it, right? I also disabled NetworkManager because I find it tends to get in the way of manually doing things.

---

### Post by mrjogo on 2009-09-04
Well, it turns out that ESSID is set in the .dat file. Even changing it to the essid of my wireless router (which is broadcasting it) won't get it to connect, though. Any thoughts?

---

### Post by vanzandtj on 2009-09-23
I have a Linksys WUSB600N adapter with this ID:
# lsusb|grep Link
Bus 001 Device 005: ID 1737:0079 Linksys 

I'm trying to use it on a Debian system with a 2.6.24 kernel.
So far, I don't have it working.

I downloaded version 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2, and applied this patch:

--- ../orig/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk      2009-08-                                                 13 03:54:04.000000000 -0400
+++ ./os/linux/config.mk        2009-09-21 21:04:31.000000000 -0400
@@ -6,10 +6,10 @@
 
 
 # Support Wpa_Supplicant
-HAS_WPA_SUPPLICANT=n
+HAS_WPA_SUPPLICANT=y
 
 # Support Native WpaSupplicant for Network Maganger
-HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
+HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
 
 #Support Net interface block while Tx-Sw queue full
 HAS_BLOCK_NET_IF=n
--- ../orig/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/usb_main_dev.c 2009-08-                                                 13 02:34:22.000000000 -0400
+++ os/linux/usb_main_dev.c     2009-09-22 17:55:44.000000000 -0400
@@ -105,6 +105,7 @@
        {USB_DEVICE(0x7392,0x7717)},
        {USB_DEVICE(0x1737,0x0070)}, /* Linksys WUSB100 */
        {USB_DEVICE(0x1737,0x0071)}, /* Linksys WUSB600N */
+       {USB_DEVICE(0x1737,0x0079)}, /* Linksys WUSB600N v2 */
        {USB_DEVICE(0x0411,0x00e8)}, /* Buffalo WLI-UC-G300N*/
        {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */
        {USB_DEVICE(0x100D,0x9031)}, /* Motorola 2770 */

The new module loads and will recognize the device, but won't scan or associate:

Script started on Wed 23 Sep 2009 07:10:54 PM EDT

# modprobe rt2870sta
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       Ralink STA  
          
# ifconfig ra0 up
# iwconfig ra0
ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:25:9c:09:96:72  
          inet6 addr: fe80::225:9cff:fe09:9672/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2000 (1.9 KiB)

# iwlist ra0 scan
ra0       No scan results

# iwconfig ra0 ap any
# iwconfig ra0
ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# exit

Script done on Wed 23 Sep 2009 07:12:36 PM EDT

After "ifconfig ra0 up", the blue light comes on.  However, iwconfig won't change settings.  (I set the ESSID in /etc/Wireless/RT2870STA/RT2870STA.dat).  I don't have an 802.11n router yet, but it should see my b/g router.  (I've left the default setting WirelessMode=5, which supports "11ABGN mixed".)

If I'm missing something, please let me know.

If I need the previous version of the driver, can someone provide a link for it?  Ralink isn't offering it any more.

---

### Post by gmatt on 2009-10-04
> **vanzandtj said:**
> I have a Linksys WUSB600N adapter with this ID:
# lsusb|grep Link
Bus 001 Device 005: ID 1737:0079 Linksys 

I'm trying to use it on a Debian system with a 2.6.24 kernel.
So far, I don't have it working.

I downloaded version 2009_0820_RT2870_Linux_STA_V2.2.0.0.tar.bz2, and applied this patch:

--- ../orig/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk      2009-08-                                                 13 03:54:04.000000000 -0400
+++ ./os/linux/config.mk        2009-09-21 21:04:31.000000000 -0400
@@ -6,10 +6,10 @@
 
 
 # Support Wpa_Supplicant
-HAS_WPA_SUPPLICANT=n
+HAS_WPA_SUPPLICANT=y
 
 # Support Native WpaSupplicant for Network Maganger
-HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
+HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
 
 #Support Net interface block while Tx-Sw queue full
 HAS_BLOCK_NET_IF=n
--- ../orig/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/usb_main_dev.c 2009-08-                                                 13 02:34:22.000000000 -0400
+++ os/linux/usb_main_dev.c     2009-09-22 17:55:44.000000000 -0400
@@ -105,6 +105,7 @@
        {USB_DEVICE(0x7392,0x7717)},
        {USB_DEVICE(0x1737,0x0070)}, /* Linksys WUSB100 */
        {USB_DEVICE(0x1737,0x0071)}, /* Linksys WUSB600N */
+       {USB_DEVICE(0x1737,0x0079)}, /* Linksys WUSB600N v2 */
        {USB_DEVICE(0x0411,0x00e8)}, /* Buffalo WLI-UC-G300N*/
        {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */
        {USB_DEVICE(0x100D,0x9031)}, /* Motorola 2770 */

The new module loads and will recognize the device, but won't scan or associate:

Script started on Wed 23 Sep 2009 07:10:54 PM EDT

# modprobe rt2870sta
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       Ralink STA  
          
# ifconfig ra0 up
# iwconfig ra0
ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:25:9c:09:96:72  
          inet6 addr: fe80::225:9cff:fe09:9672/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2000 (1.9 KiB)

# iwlist ra0 scan
ra0       No scan results

# iwconfig ra0 ap any
# iwconfig ra0
ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# exit

Script done on Wed 23 Sep 2009 07:12:36 PM EDT

After "ifconfig ra0 up", the blue light comes on.  However, iwconfig won't change settings.  (I set the ESSID in /etc/Wireless/RT2870STA/RT2870STA.dat).  I don't have an 802.11n router yet, but it should see my b/g router.  (I've left the default setting WirelessMode=5, which supports "11ABGN mixed".)

If I'm missing something, please let me know.

If I need the previous version of the driver, can someone provide a link for it?  Ralink isn't offering it any more.

Yea I have a similar problem. I found that I could change settings by changing the contents of /etc/Wireless/RT2870STA/Rt2870STA.dat , however even if I configure everything correctly in the dat file it still doesn't work for me. 


The status of this network adapter should be changed to COMPLTELEY UNSUPPORTED for v2.

---

### Post by vanzandtj on 2009-10-17
The Ralink software download page [http://eng.ralinktech.com.tw/support.php](http://eng.ralinktech.com.tw/support.php) no longer even mentions Linux.

---

### Post by vanzandtj on 2009-10-18
Hmm. must have been a temporary glitch (with either the Ralink site or my eyesight) because they are showing Linux files again: [http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2)
No RT2870USB support update since version 2.2.0.0 of Aug 20, though.

---

### Post by onytz on 2009-11-05
Hello all, 
I've followed the instructions on the first page of this thread to try to get WUSB600N working, but still no luck. I think I'm part of the way there:

```

amz@yeats:~$ lsusb
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1737:0079 Linksys 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But the led is not lighting up on the device itself.
Other info that may be relevant: I'm using crunchbang, based on ubuntu 8.10

Does anyone have any insights?
Thanks!

---

### Post by danmaster23 on 2009-11-13
Hi, I followed the steps from first post but on step 4 this is what I get:

make -C tools
make[1]: Entering directory `/home/dan/Downloads/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dan/Downloads/WUSB600N/tools'
/home/dan/Downloads/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/dan/Downloads/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/dan/Downloads/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/dan/Downloads/WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/dan/Downloads/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

I'm a pro when it comes to linux but I'm sure what the error is.

Thanks

---

### Post by SpiderTex on 2009-11-28
this is hart breaking....   I need this N nic up and running....   and I don't want to revert to XP :(

maybe this info helps a bit: I downloaded the latest driver from ralink, added the 1737:0079; added the patch; and then ran the make routine
during the make it gave warnings like a "out of range" (where can I find the log file - if exists)

---

### Post by newubu41 on 2009-12-02
I am really new to Ubuntu and have some extremely basic questions
 
**Re: Linksys WUSB600N working in hardy and ibex** 
 
 
Code:
sudo mkdir /lib/modules/<kernel version>/wirelesssudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
"Where do I find <kernel version> ?
 
 
 
Thanks

---

### Post by mizunoX on 2009-12-05
> **newubu41 said:**
> I am really new to Ubuntu and have some extremely basic questions
 
**Re: Linksys WUSB600N working in hardy and ibex** 
 
 
Code:
sudo mkdir /lib/modules/<kernel version>/wirelesssudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless
"Where do I find <kernel version> ?
 
 
 
Thanks

Fair question.  Open a terminal and type 'uname -a' (without quotes) to find it.

---

### Post by the1onlyfelix on 2009-12-21
i do not have rt2870sta.ko in WUSB600N/os/linux or anywhere in the WUSB600N folder.

---

### Post by greenblaze on 2009-12-23
I did the steps exactly as above but I dont see the ra0 interface?

---

### Post by Tlap on 2009-12-28
> **danmaster23 said:**
> Hi, I followed the steps from first post but on step 4 this is what I get:

make -C tools
make[1]: Entering directory `/home/dan/Downloads/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dan/Downloads/WUSB600N/tools'
/home/dan/Downloads/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/dan/Downloads/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/dan/Downloads/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/dan/Downloads/WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/dan/Downloads/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

I'm a pro when it comes to linux but I'm sure what the error is.

Thanks

Hi, i'm completely new to Linux but I know the Bash shell with Unix.  I decided to give Linux a try and have a WUSB600N and I went threw the directions and when running the makefile I get the exact same error.  Any ideas?  

Thanks.

---

### Post by ipatrol on 2010-01-04
I have a handy script to make all this easier:
```
#!/bin/bash
mkdir WUSB600N
cd WUSB600N
tar -xf ../WUSB600N.tar
sudo make
sudo mkdir /etc/Wireless 
sudo mkdir /etc/Wireless/RT2870STA 
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
cd ./os/linux
sudo insmod rt2870sta.ko
sudo mkdir "/lib/modules/$(uname -r)/wireless"
sudo cp rt2870sta.ko "/lib/modules/$(uname -r)/wireless"
echo "a
rt2870sta
.
w /etc/modules
q
" | sudo ed /etc/modules
echo "(-2/exit 0/)a
sudo insmod '/lib/modules/$(uname -r)/wireless/rt2870sta.ko'
.
w /etc/rc.local
q
" | sudo ed /etc/rc.local
exit 0
```

---

### Post by bcfuller on 2010-01-06
banging my head against the wall

---

### Post by bcfuller on 2010-01-06
> **danmaster23 said:**
> Hi, I followed the steps from first post but on step 4 this is what I get:
 
make -C tools
make[1]: Entering directory `/home/dan/Downloads/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dan/Downloads/WUSB600N/tools'
/home/dan/Downloads/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/dan/Downloads/WUSB600N/os/linux/Makefile
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/dan/Downloads/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
CC [M] /home/dan/Downloads/WUSB600N/os/linux/../../common/rtmp_init.o
CC [M] /home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/dan/Downloads/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
 
I'm a pro when it comes to linux but I'm sure what the error is.
 
Thanks
 
 
I am also having this issue.  Anyone find a solution yet?

---

### Post by bert4130 on 2010-01-11
I am on a netbook and dont have a usb. is there another way to get the drivers?

---

### Post by the.marion.cobretti on 2010-01-23
after reading this entire thread, [as i too am trying to enable WSU600n drivers] id just like to say mizunoX, you have the patience of a saint.  diligently helping those that have little to no linux experience is very commendable.  

id also like to say that im very pleased at all of the people using ubuntu with no linux background.  ive been a *nix user for a very long time, and to see so many people trying to learn and work outside of their normal sandbox is just very exciting.

those that are struggling just keep working at it, and soon you will be here helping other.


be well,
~marion


p.s.  thanks for the write up miz, worked perfectly for me.

---

### Post by woober on 2010-01-24
anyone there knows a alternate download site. problem is that i don't have a rapidshare account and then i'm up there is like never a nonpaying slot open. 

help please

---

### Post by ipatrol on 2010-02-06
It won't compile: "struct task_struct has no member "fsguid"

---

### Post by Claymore2106 on 2010-02-08
> **ipatrol said:**
> It won't compile: "struct task_struct has no member "fsguid"

I'm having the same problem. I have no Linux experience at all (other than what was said for the console codes, obviously), and I'm trying to get this to work. I posted on another thread here, and they didn't have an answer either. this seems to be a rather difficult problem....

---

### Post by ipatrol on 2010-02-08
Well, from what I know of C, someone probably removed a line in the aformentioned struct and forgot to remove all references to it. Certainly something to be fixed.

---

### Post by ghuber on 2010-03-01
I have a WUSB600N v2 and it is working great for me.  Here is all you have to do.

Go here and download the RT3572USB driver
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

The file you download is called 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2

expand it with the command

"tar xjf 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2"

open the file os/linux/config.mk and edit the following lines:
Change HAS_WPA_SUPPLICANT=n
to     HAS_WPA_SUPPLICANT=y

and

Change  HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to      HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Next edit the file common/rtusb_dev_id.c and add the USB ID of the card to it.

{USB_DEVICE(0x1737,0x0079)}, /* WUSB600Nv2 */

sudo make

sudo make install

reboot and your done.

If you have added the USB device to any other drivers following other threads you will want to either remove that line and recompile those drivers OR black list those drivers.  After doing the above this NIC is working great for me in Ubuntu 9.10 and getting N speeds.

---

### Post by sylenceone on 2010-03-09
Thanks a mil ghuber. That worked for me! Getting N speed!

---

### Post by ankith13 on 2010-03-17
for the people who are getting the error as

 
/home/dan/Downloads/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’

they probably have the driver installed but the problem is there are multiple drivers...
just try to blaclist other drivers 

just give :

sudo gedit  /etc/modprobe.d/blacklist.conf

and add the threelines to the end of the file...
 


blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib


try it out and let me know if there is a problem......

---

### Post by dea.leal on 2010-03-18
Hello everyone, 
I am very very new to ubuntu, so please excuse me if I ask for some very basic help. I have a dual boot computer, with Windows XP and UBUNTU 9,1
I have read through 2 threads on the WUSB600N adapter. Some of the tips read like greek to me, though.
I have downloaded the WUSB600N.tar file. I have copied that and then extracted the file to my desktop.
I tried then going into the terminal and navigating to the folder where the files were extracted. I can't get past this: the computer says there is no such folder.
I have typed in "dir" to see a list of the directories, but it just won't work. 
Here is a print screen shot.
I would really appreciate it if anyone could help me.
Andrea.

> **impala79 said:**
> Great thread misunoX! I followed your instructions to install the driver and then to get it to load on startup. I restarted the computer, and dmesg told me the driver was loaded (I should mention I didn't even have the hardware connected yet)

I then went out and picked up WUSB600N from staples, plugged it in, and it worked perfectly. Ibex detected it, asked for permission to start up a Network Protocol program to get wireless going, and then it detected all of the routers in range. 

Now I'm connected very stably at 270 Mb/s. Very cool. 


Rmcellig, to help you wout with steps 3 and 4:

To open your terminal go to Applications -> Accessories -> Terminal

Once there, to navigate to your created directory just type it's path. I had mine sitting on the desktop, so I typed

cd Desktop/WUSB600N

Hit enter and you'll be in that directory. now for step 4. simply type

sudo make

it will ask for your admin password. Type it in, but note that in the terminal when you enter a password, nothing appears in the terminal! It's like you're typing ghost letters or something! so just type in your password and hit enter, and a whole lot of stuff should appear in the terminal window. Wait for this to stop. When it does you'll have the regular terminal command line back.

Now for step 5 just type those three sudo commands and hit enter after each.

For step 6 first type

cd /os/linux

Then type that sudo insmod... command. 

To have the module load at startup, follow the post at the bottom of page 1. I think it'll be easy once you've got a handle on what you hopefully successfully did above!

---

### Post by bkratz on 2010-03-18
Please see your other thread posting.

---

### Post by ericson578 on 2010-03-24
I got my WUSB600N v1 linksys wireless card working by adding the line "blacklist rt2800usb" to  /etc/modprobe.d/blacklist.conf several weeks ago.

I just did an update today and my wireless stopped working, so I commented out that line (put a # at the beginning of the line if you are a beginner) rebooted and it started working again.  One of the updates must have added support for this device? Not sure, but just in case you did the same fix as me and it suddenly stopped working I hope this helps :D

---

### Post by Soul_Architech on 2010-03-26
I just installed Ubuntu 9.10 and am trying to get my Linksys WUSB600N working. After I typed in the command sudo make most of it came through fine but I had some errors. 



[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151480&stc=1&thumb=1&d=1269580539[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=151480&d=1269580539")








Here is a screen shot. Any ideas on how I should proceed? Thank you!

---

### Post by MCVenom on 2010-03-29
> **ghuber said:**
> I have a WUSB600N v2 and it is working great for me.  Here is all you have to do.

Go here and download the RT3572USB driver
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

The file you download is called 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2

expand it with the command

"tar xjf 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2"

open the file os/linux/config.mk and edit the following lines:
Change HAS_WPA_SUPPLICANT=n
to     HAS_WPA_SUPPLICANT=y

and

Change  HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to      HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Next edit the file common/rtusb_dev_id.c and add the USB ID of the card to it.

{USB_DEVICE(0x1737,0x0079)}, /* WUSB600Nv2 */

sudo make

sudo make install

reboot and your done.

If you have added the USB device to any other drivers following other threads you will want to either remove that line and recompile those drivers OR black list those drivers.  After doing the above this NIC is working great for me in Ubuntu 9.10 and getting N speeds.
When all else failed, this worked for me; for those still having compiling errors (particularly fsgid/fsuid issues), try this. :D

---

### Post by ergiga on 2010-04-10
> **mizunoX said:**
> 

Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.

The wireless card should now be working.


I can't find the file rt2870sta.ko...

Is it in downloaded folder or in my system?

Please help!

---

### Post by rachyl on 2010-04-14
-

---

### Post by Ameades on 2010-10-14
Does anyone know whats gone on with the WUSB600N and it working in Ubuntu 10.4?  I plug it in and it seems to work 'out of the box' because it is recognized, but it only sees a select few wireless networks in my area.  Unfortunately my home one is not part of those select few...

---

### Post by ergiga on 2010-10-15
> **Ameades said:**
>   Unfortunately my home one is not part of those select few...

Same problem and I dont know why :(

---

### Post by mizunoX on 2010-10-23
Guys, if you're having trouble compiling the driver from source, try the changes to source outlined here:  [http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870&page=23](http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870&page=23) Post #221

---

### Post by Jables2121 on 2010-12-07
i have tried everything to get this to work and every time i get to 
>  Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.it displays  the error 
> `rt2870sta.ko': No such file or directorycould you explain what to do from here on as well plz.

---

### Post by UltraAnders on 2011-09-02
Pointed to this thread from the [Ubuntu help page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB"). Does this apply for 11.04? Thanks.

---

### Post by RonanRaven on 2011-09-03
> **UltraAnders said:**
> Pointed to this thread from the [Ubuntu help page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB"). Does this apply for 11.04? Thanks.

WUSB600N hardware v1 using 11.04 should have working drivers out of the box (I've tested it with 11.04 server, successfully connects via wpa and dhcp using the wext driver)

The problem I'm experiencing is that the max transfer speed I've been able to obtain is <2mb/s even though I have good signal, its connected to a usb 2.0 and shouldn't be having problems.

so! in other words; connectivity is good, but transfer rate is not.

*EDIT: Nevermind... had a derp moment, i had to manually set the rate to auto. end up getting 6x the speed back! ~1.7mb/s to ~7mb/s "sudo iwconfig wlan0 rate auto"

---

### Post by UltraAnders on 2011-09-06
Thanks for the reply. It does work out of the box, but the connection is very flaky. It also doesn't detect my wireless N network, which is the one I really need to connect to.

At the moment I'm using the compat-wireless-2011-08-04 drivers. A lot more reliable but still no wireless N network detected.

The attachment in the first thread doesn't want to compile on my machine (11.04). It was slightly confusing because a compiled RT2870STA.dat file is included in the tar, but it's for which ever version it was was compiled on in 2008.
```
sudo make
make -C tools
make[1]: Entering directory `/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/tools'
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.38-11-generic/build SUBDIRS=/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/md5.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/mlme.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/mlme.c: In function &#8216;BssTableSetEntry&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/mlme.c:3860:39: warning: operation on &#8216;Tab->BssOverlapNr&#8217; may be undefined
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/mlme.c:4259:1: warning: the frame size of 1576 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/action.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_data.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_data.c: In function &#8216;RTMP_FillTxBlkInfo&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_data.c:713:1: warning: label &#8216;FillTxBlkErr&#8217; defined but not used
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_sync.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/eeprom.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_info.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_wpa.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_wpa.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/cmm_wpa.c:836:1: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/dfs.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../common/spectrum.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/assoc.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/aironet.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/auth.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c:1393:1: warning: the frame size of 1308 bytes is larger than 1024 bytes
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c:934:1: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c:675:1: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sync.c:533:1: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/sanity.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/connect.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/connect.c:351:1: warning: the frame size of 1596 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/wpa.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/wpa.c: In function &#8216;CCKMPRF&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../sta/wpa.c:1848:1: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_linux.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_linux.c:1043:1: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c: In function &#8216;RTMPReadParametersHook&#8217;:
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c:928:20: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c:929:20: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c:930:9: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c:930:24: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c:1593:9: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.c:1594:9: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
make[2]: *** [/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/andersharrison/Setup_Files/WUSB600N/Ubuntu_Forum_Modified_WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2

```

---

### Post by UltraAnders on 2011-10-03
Link to a solution for the compile error, which will also get wireless N networks showing up, can be found in this [post]("http://ubuntuforums.org/showpost.php?p=11306587&postcount=349"). Big thanks to Arraen :)

---

