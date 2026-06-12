---
title: "Problematic USB wireless adapter"
date: 2023-06-07
forum: Networking &amp; Wireless
---

### Post by tinman456 on 2023-06-07
Hi again folks. Well as a new Ubuntu user everything is going pretty well so far. I am now using it on my main laptop and have done away with Win10 (up to now).

My new and intractable problem is that I have this Realtek USB wireless adapter that I cannot seem to get to work. This is a different one than what Morbius kindly sorted out for me on my other laptop (again many thanks).

When I do an lsusb this is the output for the adapter in question:

[B]Bus 001 Device 004: ID 0bda:b812 Realtek Semiconductor Corp. RTL88x2bu [AC1200 Techkey]
[/B]
and try as I might i just cannot get a driver to install. I have ran basically all the scripts I can find on the internet and even downloaded a PPA repository from fostips.com that includes a driver for RTL8822bu but with no luck. So I'm now hoping I can get the help I need from you worthy folks on the forum.

Thanks in advance.

---

### Post by chili555 on 2023-06-07
Please try this: [https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

If you need a step-by-step, please post back and we'll be happy to help.

---

### Post by tinman456 on 2023-06-08
Hi and good morning chili555 and thanks for your welcome reply. Now reading up on the info you sent in the link I noticed where they advised not to try an install without first removing any drivers you you may have installed previously. I searched for how to do that and the results were not satisfactory for my present level of expertise.

I did a sudo dkms status and it came up with 'rtl88x2bu/5.3.1: added'. I'm kind of stuck there as 1) I'm not sure what that means and 2) what, if anything, to do about it. 

Further info about my present USB wireless adapter - it is an RTL8812bu which I have gleaned to be a single-function chipset

I'd very much appreciate any further help you can give me regarding finding and removing, if needed, an already installed driver for that adapter.

Thanks.

P.S. As I was further researching I found another similar post from you where you were replying to jjjremy and I tried some of the things you mentioned but it hasn't worked for me. I guess I still don't know if I really do have a driver to be uninstalled or not.

---

### Post by chili555 on 2023-06-08
> sudo dkms status and it came up with 'rtl88x2bu/5.3.1: added''Added' is not the same thing as installed; however, in the interest of cleanliness, let's remove it anyway:

```
sudo dkms  remove rtl88x2bu/5.3.1 --all
```

> Further info about my present USB wireless adapter - it is an RTL8812bu which I have gleaned to be a single-function chipsetWe know everything we need from the usb.id:  ID [COLOR="#FF0000"]0bda:b812[/COLOR] Realtek Semiconductor Corp. RTL88x2bu [AC1200 Techkey]. I compiled the driver I link to above and the alias field reports:

```
$ modinfo 88x2bu.ko | grep B812
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]B812[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*
```I am confident that will be the driver you need. 

Please post back if you get stuck.

---

### Post by tinman456 on 2023-06-08
Hi and good morning chili555 and thanks for your welcome reply. Now reading up on the info you sent in the link I noticed where they advised not to try an install without first removing any drivers you you may have installed previously. I searched for how to do that and the results were not satisfactory for my present level of expertise.

I did a sudo dkms status and it came up with 'rtl88x2bu/5.3.1: added'. I'm kind of stuck there as 1) I'm not sure what that means and 2) what, if anything, to do about it. 

Further info about my present USB wireless adapter - it is an RTL8812bu which I have gleaned to be a single-function chipset

I'd very much appreciate any further help you can give me regarding finding and removing, if needed, an already installed driver for that adapter.

Thanks.

---

### Post by tinman456 on 2023-06-08
I'm getting 'ERROR: Module 88x2bu.ko not found'

---

### Post by chili555 on 2023-06-08
> **tinman456 said:**
> I'm getting 'ERROR: Module 88x2bu.ko not found'At what point? After you did sudo ./install-driver.sh? Or when?

You only need the .ko extension if you are examining with modinfo a module built but not necessarily installed, located in the current working directory. If you are examining an *installed*, likely with dkms, module, then:

```
modinfo 88x2bu | grep B812
```Not also that letters are always capitalized in alias fields; b812 is not the same as B812.

---

### Post by tinman456 on 2023-06-08
Immediately as I run the code. As below-
 
avh@avh-dv4:~$ modinfo 88x2bu.ko | grep B812
alias:          usb:v0BDApB812d*dc*dsc*dp*icFFiscFFipFFin*
modinfo: ERROR: Module 88x2bu.ko not found.
alias:: command not found


and:

avh@avh-dv4:~$ modinfo 88x2bu | grep B812
modinfo: ERROR: Module 88x2bu not found.

---

### Post by chili555 on 2023-06-08
Is the module *installed* or simply added?

```
history | grep dkms
sudo dkms status
```

---

### Post by tinman456 on 2023-06-08
This is the output chili555: I can't thank you enough!

avh@avh-dv4:~$ history | grep dkms
sudo dkms status
    5  sudo apt install -y build-essential dkms git bc
   12  sudo apt install -y build-essential dkms git bc
   19  sudo apt install -y build-essential dkms git bc
   42  sudo apt-get install build-essential dkms git
   47  sudo dkms add -m rtl88x2bu -v ${VER}
   48  sudo dkms build -m rtl88x2bu -v ${VER}
   49  sudo dkms install -m rtl88x2bu -v ${VER}
   52  sudo apt-get install -y dkms git
   60  sudo apt-get install build-essential dkms git
   63  VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
   65  sudo dkms add -m rtl88x2bu -v ${VER}
   66  sudo dkms build -m rtl88x2bu -v ${VER}
   67  sudo dkms install -m rtl88x2bu -v ${VER}
   73  sudo dkms add -m rtl88x2bu -v ${VER}
   74  sudo dkms build -m rtl88x2bu -v ${VER}
   75  sudo dkms install -m rtl88x2bu -v ${VER}
   80  sudo dkms add -m rtl88x2bu -v ${VER}
   81  sudo dkms build -m rtl88x2bu -v ${VER}
   82  sudo dkms install -m rtl88x2bu -v ${VER}
   87  sudo dkms status
   94  sudo dkms status
  110  sudo dkms status
  125  sudo dkms  remove rtl88x2bu/5.3.1 --all
  144  history | grep dkms
  145  sudo dkms status
  147  sudo dkms status
  148  history | grep dkms
  149  sudo dkms status
  152  sudo dkms status
  153  history | grep dkms

---

### Post by chili555 on 2023-06-08
Please include: ```
sudo dkms status
```

And then:

```
history | grep install
```

---

### Post by tinman456 on 2023-06-08
sorry... here you go:-

avh@avh-dv4:~$ history | grep install
    1  sudo apt-get install synaptic
    5  sudo apt install -y build-essential dkms git bc
    9  sudo make install
   12  sudo apt install -y build-essential dkms git bc
   16  sudo make install
   19  sudo apt install -y build-essential dkms git bc
   23  sudo make install
   34  sudo apt update && sudo apt install --install-recommends winehq-stable
   39  sudo apt install libfuse2
   42  sudo apt-get install build-essential dkms git
   49  sudo dkms install -m rtl88x2bu -v ${VER}
   52  sudo apt-get install -y dkms git
   57  sudo ./install-driver.sh
   60  sudo apt-get install build-essential dkms git
   67  sudo dkms install -m rtl88x2bu -v ${VER}
   75  sudo dkms install -m rtl88x2bu -v ${VER}
   82  sudo dkms install -m rtl88x2bu -v ${VER}
   98  sudo make uninstall
  107  sudo make uninstall
  119  sudo apt install ndiswrapper-common ndiswrapper-utils-1.9
  123  sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
  155  history | grep install

---

### Post by chili555 on 2023-06-08
I see no evidence at all that you installed the driver I linked. Please do:

```
git clone [https://github.com/morrownr/88x2bu-20210702.git](https://github.com/morrownr/88x2bu-20210702.git)
cd 88x2bu-20210702
sudo ./install-driver.sh
```

This takes a few moments, please be patient.

When the terminal says: >  Do you want to edit the driver options file now? (recommended) [Y/n] Type n and press Enter.

When it says: >  Do you want to apply the new options by rebooting now? (recommended) [Y/n] Type n and press Enter.

Is the driver now present?

```
modinfo 88x2bu
```

Load it:

```
sudo modprobe 88x2bu
```Is your wireless now working?

---

### Post by tinman456 on 2023-06-08
How amazing! I hope one day to have as much knowledge.

Yes my friend Chili555 it is indeed working. I have already disconnected the Ethernet and I am using my w/less adapter at 5GHz as we speak......

Cheers and blessings.

Anthony

---

### Post by chili555 on 2023-06-08
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by tinman456 on 2023-06-09
Yes, I marked it solved (with many thanks).

I have been going through your commands line by line and the only one I can't completely figure out is '[COLOR=#000000][FONT=&quot]git clone [/FONT][/COLOR][https://github.com/morrownr/88x2bu-20210702.git](https://github.com/morrownr/88x2bu-20210702.git)'.

Can you point me to somewhere I can read about it? I really respect and admire the knowledge you folks have acquired and especially your willingness to share that with our (clueless) community.

---

### Post by chili555 on 2023-06-09
Github is simply a repository for computer code; in this case, a wireless driver maintained by user @morrownr. Anyone can see and read the code. 

The command &#8216;git clone&#8217; issued on your computer simply copies over the specific repository, in this case, 88x2bu-20210702, to your computer. So now you have a local copy of the entire driver source code. You can read it, modify it and even update it as needed.

With the code in place on your computer, it can be compiled against your specific kernel version, gcc compiler, etc.  

You can read valuable information and the exact installation process in the aptly named README document that is included.

Please see: ```
man git
```

---

### Post by tinman456 on 2023-06-09
Thank you...

---

