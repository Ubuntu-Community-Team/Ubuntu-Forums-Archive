---
title: "&quot;connection interrupted&quot; message when logging into web sites."
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by recon69 on 2008-12-02
Hi, 

   Just posting this as a FYI. I was having intermittent problems logging into web pages using Firefox and Ubuntu 8.04. my internet connection was working well otherwise. but when i tried to log into sites like hotmail, gmail, yahoo, or using pastebins or attaching files to forum posts I would get a "connection interrupted" message or a blank page after about 1 minute of waiting. Strangely other people sharing the connection using windows seemed not to experience the problem as much (not so sure about this as I dont really know what they where using)

   This problem would come and go and i could find no reason. But after contacting my ISP the problem was identified. It seem that after upgrading my internet service I was receiving a ADSL 2 (12mb) service while my router ( a belkin) was only able to handle adsl 1. My Isp changed my profile to a 8mb connection and the problem went away. 

   Just posting this as other people my find it useful if they experience similar problems.  

regards

---

### Post by recon69 on 2008-12-03
Well, I spoke to soon in my joy at thinking it was solved, the problem returned about 2 hours later. 

   My current hypothesis is that a windows machine that is on the same wireless network has a virus and it's interfering with http post and secured packets on the network. I come to this conclusion as the problem only happens when a certain windows computer is turned on, and goes away when it's turned off and the router is rebooted. 

   I would have updated this sooner but I could not post a reply till the virus-ed computer was powered off.

regards

---

### Post by recon69 on 2008-12-04
Well, wrong again. Checked my connection when the supected computer was on and had no problems. 

  So still guessing. I'm left with this idea, while I was experiencing this problem the firestarter firewall was reporting a open connection to a google server, this connection was on port 80 and had no named process. wireshark was picking up occasional re-transmit request to this server. This connection was still reported as open even after computer reboot and I could see no reason for it to be there. I could reboot and immediately open firestarter and a connection would be reported. I could find no other indication that there was an active connection to that google server.

  As to the cause, my computer occasionally experiences kernel panics which seem to be liked to viewing several web sites in firefox tabs simultaneously (have never been able to find an exact cause to this either). I think that when the kernal panic happen it's leaving a incomplete request to that google server which later interferes with other secured web pages.

  I will have to wait till the occurs again to see if this is the cause.

regards

---

### Post by recon69 on 2008-12-11
Well, found out about the strange connections with no process from firestarter , check bug [https://bugs.launchpad.net/bugs/112334](https://bugs.launchpad.net/bugs/112334) , so thats a dead end. Found another bug report that seem to be closely related [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209359) , but this not the full story either because i'v got 2 types of behavior , one is the "connection interrupted" bug, then when I dont get connection interrupted and can actually login I get kernel panics after a while. I had my isp put my connection back to adsl2 (12mb) and I can now sort of use secured sites.

  As to what next I don't know, I just consider this likely to stop me using Ubuntu as half an internet connection or a system that continually crashes is just not going to cut it. was actualy able to check my e-mail today but had 3 kernel panics while doing it. 

 regards

---

### Post by scpatl4now on 2009-01-02
I'm not sure where this problem lies, but its been driving me nuts!  I just started getting these messages a couple of weeks ago.  Its not Ubuntu specific as its happened on my Windows machine as well.  I've just started researching, but it seems to have been reported with IE as well...smells like fishy ISP stuff to me

---

### Post by recon69 on 2009-01-03
Still getting both problems, some web pages not loading intermittently and regular kernel panics.
  Have tried installing 8.10 with did not fix eather of the problem. and done several clean installs of 8.04 with no change.
  Regarding the kernel panics I'm guessing that kernel panics are caused by my wireless card driver (rt61pci). seems it's buggy. from reading some info on the web seem there are several implementations of these drivers and that recently they have made it into the kernel (2.6.27 from memory). unfortunately the current kernel(2.6.24-22-generic) in 8.04 is still using the older drivers which are buggy. 
  My main hope is that I'm planning to get a new computer soon and hope that I will escape these issues that way. 

regards

---

