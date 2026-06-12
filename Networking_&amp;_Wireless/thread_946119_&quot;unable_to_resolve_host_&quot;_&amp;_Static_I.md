---
title: "&quot;unable to resolve host &quot; &amp; Static IP problems"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by nonzer0 on 2008-10-13
I went through at least fifty pages in the ubuntu forums and google on setting up a static ip address.  Every page involves writing tens of lines of code in terminal. I can't seem to go to system > Adminstration > Network and set it up in there, under "Static IP" like I could in windows.  If I setup the static IP, the internet no longer works.  The settings must be Auto Config (DHCP)

After so many hours(this is actually months of trying and giving up repeatedly), I think I got it to work. 

NOW.  I've been getting errors in Terminal for a while any time I try to do "sudo something something" I receive the error "unable to resolve host <hostname>." Now I have spent hours and hours trying to solve this, and I can't.  Every thread says that I must deleter my host name from the Host name feild under the General tab in network settings (it just comes right back after opening and closing) edit my /etc/hosts file.  OK, but my hosts file is missing the first two lines of the info others hosts file contains.  

Example: standard hosts file:
"127.0.0.1 localhost
127.0.1.1 T-61

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts "

My hosts file contains the following text:
"# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

Does anyone know why the first two lines are missing.  I am afraid if I restart my computer I will be locked out.  One person said he got locked out of his computer and couldn't log into ubuntu.

What have I done wrong! What causes this! and how the hell do I know if I have a static IP!?  Why does setting up a static IP address involve writing 28 lines of tripped out code when the option is available in the Network options, only it doesn't work?!?  ](*,) :lolflag:

P.S. This is extremely frustrating and stupid.  If the option to set up a Static IP address is under the Network settings, it should work.  EXTREMELY FRUSTRATING!!!
And I wouldn't be posting this if I hadn't looked.  No ones hosts file seems to be missing the first two lines.
... Also, I thought the 127.0.0.1 address pertained to using a proxy such as tor/vidalia... :confused:

I appreciate any help or guidance.

---

### Post by cariboo on 2008-10-13
Open a Applications-->Accessories-->Termianl and type:

```
sudo nano /etc/hosts
```

then add the following to lines to the top of the file:

```
127.0.0.1 localhost
127.0.1.1 T-61

```

This is assuming the name of your computer is T-61, if your computer name is something different use it instead.
If your are not sure what your computers name is, open another terminal and type:

```
hostname
```

This will echo back your computer's name.

When your done your /etc/hosts file should look like this:

```
127.0.0.1 localhost
127.0.1.1 T-61

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhost
```

Press Ctrl-o to save the file, then Ctrl-x to exit the editor

Once you have done the above you should be able to go into network manager and setup a static ip addess.

Jim

---

### Post by Dirty Ole on 2008-10-13
I had the same problem, setting up a static IP. I gave up network-manager and installed wicd network manager and now I am happy as a fox. 

Instructions and repository links [here]("http://wicd.sourceforge.net/").

---

### Post by american.swan on 2008-10-13
I would like to "bump" this post because I have had similar problems, but I've never been locked out.  
 
> **nonzer0 said:**
> I went through at least fifty pages in the ubuntu forums and google on setting up a static ip address. Every page involves writing tens of lines of code in terminal. I can't seem to go to system > Adminstration > Network and set it up in there, under "Static IP" like I could in windows. If I setup the static IP, the internet no longer works. The settings must be Auto Config (DHCP)
 
After so many hours(this is actually months of trying and giving up repeatedly), I think I got it to work. 
 
NOW. I've been getting errors in Terminal for a while any time I try to do "sudo something something" I receive the error "unable to resolve host <hostname>." Now I have spent hours and hours trying to solve this, and I can't. Every thread says that I must deleter my host name from the Host name feild under the General tab in network settings (it just comes right back after opening and closing) edit my /etc/hosts file. OK, but my hosts file is missing the first two lines of the info others hosts file contains. 
 
Example: standard hosts file:
"127.0.0.1 localhost
127.0.1.1 T-61
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts "
 
My hosts file contains the following text:
"# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"
 
Does anyone know why the first two lines are missing. I am afraid if I restart my computer I will be locked out. One person said he got locked out of his computer and couldn't log into ubuntu.
 
What have I done wrong! What causes this! and how the hell do I know if I have a static IP!? Why does setting up a static IP address involve writing 28 lines of tripped out code when the option is available in the Network options, only it doesn't work?!? ](*,) :lolflag:
 
P.S. This is extremely frustrating and stupid. If the option to set up a Static IP address is under the Network settings, it should work. EXTREMELY FRUSTRATING!!!
And I wouldn't be posting this if I hadn't looked. No ones hosts file seems to be missing the first two lines.
... Also, I thought the 127.0.0.1 address pertained to using a proxy such as tor/vidalia... :confused:
 
I appreciate any help or guidance.

---

### Post by nonzer0 on 2008-10-13
> **cariboo907 said:**
> Open a Applications-->Accessories-->Termianl and type:

```
sudo nano /etc/hosts
```

then add the following to lines to the top of the file:

```
127.0.0.1 localhost
127.0.1.1 T-61

```

This is assuming the name of your computer is T-61, if your computer name is something different use it instead.
If your are not sure what your computers name is, open another terminal and type:

```
hostname
```

This will echo back your computer's name.

When your done your /etc/hosts file should look like this:

```
127.0.0.1 localhost
127.0.1.1 T-61

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhost
```

Press Ctrl-o to save the file, then Ctrl-x to exit the editor

Once you have done the above you should be able to go into network manager and setup a static ip addess.

Jim

I really shouldn't be messing with this right now, seeing as how I have a final at 4pm, but anywayz...
I will try that cariboo...

Also, thank you Dirty O.  I can't beleive I never came across WICD in any thread with people having issues with setting up a static ip.

I will let you all know if the problem is solved..

---

### Post by nonzer0 on 2008-10-14
I am curious, should I edit my hosts file?  Is it normal for the first two lines to be missing.  Do I risk making my system unoperable?  
Is there a reason why the first two lines, which appear to be in everyone elses hosts file, be missing in mine?

If I indeed need to edit my hosts file and my localhost name is dreamweaver87, should my hosts file look like this 

127.0.0.1 localhost
127.0.1.1 dreamweaver87
...

I am just being cautious about changing system files.

---

### Post by Iowan on 2008-10-14
When I'm concerned about changing system files, I make a backup via **sudo cp filename filename.bak** In your case: **sudo cp /etc/hosts /etc/hosts.bak** Then **sudo nano /etc/hosts** should let you edit the file.  CTRL-O will save changes, CTRL-X will exit. 
(Guess that was previously mentioned)

---

