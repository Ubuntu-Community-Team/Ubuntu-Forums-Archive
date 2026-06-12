---
title: "Onboard Marvell NIC not recognized"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by sonicdevo on 2007-02-27
I've just done an install of Ubuntu 6.10 Desktop on my new PC, and my first step is to try and get the onboard lan adapter working.  I asked in #ubuntu, and they told me to run a sky2 modprobe, but it didn't find my nic.  I keep coming back to recompiling the kernel to get it working, but as a novice user it's kinda scary.  Tell me what you think.

My motherboard is a [Gigabyte 965P-DS3]("http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=2456&ProductName=GA-965P-DS3"), and from my motherboard's manual I can tell that my onboard nic is "Marvell 88E8056."  I've found what I believe to be the linux driver for the Marvell controller [here]("http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36").  However, the [readme]("http://paste.ubuntu-nl.org/7872/") file says I'll need the kernel source, header files and gcc.  Do I need the source for my current kernel (2.6.17-11-generic) or should I build/install a newer one? (I found a post on the forums where a user claimed that getting the 2.6.19 kernel allowed the nic to be found and work.)

Thanks for any help you're able to provide!

---

### Post by chili555 on 2007-02-27
I think the sky2 module is buggy in kernel 2.6.17. Here is a post that may help you.

[http://www.ubuntuforums.org/showthread.php?t=365385&highlight=yukon](http://www.ubuntuforums.org/showthread.php?t=365385&highlight=yukon)

See post #9 and 11.

---

