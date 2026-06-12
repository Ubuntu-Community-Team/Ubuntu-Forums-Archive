---
title: "No internet in VMWare"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by underworld288 on 2007-03-03
I just installed VMWare Server on my Ubuntu 6.10 computer and I have all the files that are needed installed, or at least I think I do, and when I start the Windows XP Pro vm it says 

"Could not open /dev/vmnet0: No such file or directory
Virtual device Ethernet0 will start disconnected."

does anyone have any idea on anything that could cause this?

thanks

---

### Post by scxtt on 2007-03-03
is vmnet0 listed in a "sudo /sbin/ifconfig"?  you should only need it if you're using NAT or something that's not bridged (assuming you use a router) ... i don't even have a vmnet* anymore since i use bridged and assign my VMs IPs from my router ...

---

### Post by underworld288 on 2007-03-03
no but eth0 is, which is what i use to connect to the Internet. How would I go about getting vmware to recognize and use that?

---

### Post by scxtt on 2007-03-03
if you don't have a vmnet* listing for ifconfig, you should still be able to use a bridged connection - which you can select in the config for the VM itself (for its ethernet device) ... i'd then assign it a static IP on your network ... if the host's eth0 is 192.168.0.1, assign it something like 192.168.0.2 (as long as that's not used anywhere else) ...

---

### Post by underworld288 on 2007-03-03
ok... how do i set a static ip, keep in mind that i am using vmware server 1.0.2.

---

### Post by scxtt on 2007-03-03
you'll do that via the OS that is running in your VM (windows xp pro, in this case)

here's an example (there are IP differences of course):

[http://www.answers.vt.edu/ask4help/connection/vtkb697.htm](http://www.answers.vt.edu/ask4help/connection/vtkb697.htm)

---

### Post by underworld288 on 2007-03-03
oh, i thought you ment set up a static ip through vmware server. ok well anyway I skipped a step first how do i enable using eth0 for the vm, i am using a bridged connection and I set up the static ip and still no internet.

---

### Post by scxtt on 2007-03-04
you have the device added and connected via vmware server?  it doesn't complain about the device at VM boot?  and it shows up in windows after boot? (seems like that is what you're saying, if you can configure it ;)) ... only other thing i can think of is that it isn't enabled in windows - or maybe conflicting IP #'s ...

---

