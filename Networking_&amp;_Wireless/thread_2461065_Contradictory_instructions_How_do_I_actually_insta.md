---
title: "Contradictory instructions: How do I actually install this driver?"
date: 2021-04-23
forum: Networking &amp; Wireless
---

### Post by dora5 on 2021-04-23
I have three different sets of instructions on how to install the driver for a usb adapter.

Note that the location and name of the file differ a lot.   And it would help to know what to call it and where to find it since the instructions at [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au) are as clear as mud.


First version.   Not clear why I have to do all three steps.

1.  git clone [https://github.com/abperiasamy/rt18812AU_8821AU_linux](https://github.com/abperiasamy/rt18812AU_8821AU_linux)  ---- fetch git repository
cd rt18812AU_8821AU_linux     --- navigate to folder
make  ----  compile the folder
sudo make install  -----  install the compiled folder


2.  cd ~/rt18812AU_8821AU_linux    --- navigate to the folder
sudo make uninstall    
make clean
sudo cp -R ~/rtl8812AU_8821AU_linux  /usr/src/rtl8812AU_8821AU_linux-1.0     
sudo dkms install -m rtl8812AU_8821AU_linux -v 1.0


Then run sudo dkms install -m rtl8812AU_8821AU_linux -v 1.0 again and it should say thta the driver is already installed


3.  sudo apt-get install build-essential git
git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
cd rt18812au
make
sudo make install
sudo modprobe 8812au


sudo restart

Second version was in an Amazon answer on how to get one of the adapters to work, and it pretty much seems to say to do step 3 and nothing else.

sudo apt-get update
sudo apt-get install linux-headers-generic  build-essential git
git clone [https://github.com/abperiasamy/rtl8812AU_8821U_linux.git](https://github.com/abperiasamy/rtl8812AU_8821U_linux.git)
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe rtl8812au

The clear as mud instructions at github seem to say to use a "new" DKMS procedure?  Do I HAVE to use the new DKMS procedure?  I'd rather not if I can avoid it, seems anything but straightforward.

Copy driver source to /usr/src/8812au-4.2.3


Then add it to DKMS


sudo apt-get install dkms 
sh
sudo dkms add -m 8812au -v 4.2.3
sudo dkms build -m 8812au -v 4.2.3
sudo dkms install -m 8812au -v 4.2.3
sudo make dkms_install


check with 
sh
sudo dkms staus


automatically load at boot:
sh
echo 8812au  | sudo tee -a /etc/modules

The actual line with sh says, ''''sh   which looks like I need to know what each apostrophe stands for.  Exactly what do I type where it says ''''sh?

Thanks!

---

### Post by jeremy31 on 2021-04-23
Moved to Networking & Wireless, please post results from terminal for ```
lsusb; mokutil --sb-state
```
There is a chance that any of the instructions will work, however I would recommend using dkms as it will automatically compile the driver when a new kernel is installed

---

### Post by dora5 on 2021-04-23
Thanks - what does the line '''sh mean?    It appears all three times I have it in the instructions copied from github.   Does it mean anything at all or is it just a placeholder?

I need to know what to actually enter - if anything.

I thought sh runs a script.   Makes no sense in the above context.

---

### Post by TheFu on 2021-04-23
sh runs the program "sh" which must be in your PATH. It probably is.  "sh" is the Bourne Shell, named after a famous Unix guy. 

Basically, running a shell inside a shell as instructed is probably (I don't really know) a way to ensure the default shell (bash on Ubuntu) doesn't get used and avoids some differences between bash and sh command interpretations. That's my guess.  If you happen to be using tcsh or zsh or pdksh or one of the 50 other shells, this would probably matter much more. 
[https://en.wikipedia.org/wiki/Comparison_of_command_shells](https://en.wikipedia.org/wiki/Comparison_of_command_shells)

I've always tried to avoid these problems by purchasing hardware that is well-supported already and doesn't need any extra effort. Long, long ago, I was burned multiple times buying hardware that either was not supported AND would never be supported, or getting hardware that claimed support, but wasn't currently supported in the kernel.  For me, avoiding future hassles is worth $25 extra to get fully supported hardware from the start.

---

### Post by dora5 on 2021-04-23
What an idea.  But the only wireless adapter that Amazon reviews say actually don't need a driver installed in Ubuntu have speed 150 mbps on the 2.4 channel.

---

### Post by dora5 on 2021-04-24
I've installed the driver at home but not tested it as adapter is on the computer I actually need to use it on at work.

If anyone should refer to this discussion to install the older series Realtek wirelss drivers, the correct url for the git clone statement is:

 git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)

It's in the upper right corner of the github page for that driver.

Try something else and you get told to log into the repository.

---

### Post by morrownr on 2021-04-24
If you are sure you have a 8812au chipset based adapter then...

[https://github.com/morrownr/8812au](https://github.com/morrownr/8812au)

If you are tired of Realtek based adapters then...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

### Post by morrownr on 2021-04-24
> **dora5 said:**
> What an idea.  But the only wireless adapter that Amazon reviews say actually don't need a driver installed in Ubuntu have speed 150 mbps on the 2.4 channel.

Hmmm... how about you run over to this site...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

It knows a lot more about USB WiFi adapters on Linux than Amazon does. There is a link to this site in the first stickied message in this list.

---

