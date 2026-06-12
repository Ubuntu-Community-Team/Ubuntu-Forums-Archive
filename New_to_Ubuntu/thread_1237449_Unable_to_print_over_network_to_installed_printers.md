---
title: "Unable to print over network to installed printers"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by outerheaven11 on 2009-08-11
I have three network printers: 

Sharp MX4501N x 1
Sharp MX350N x 2

All are online and working with my Windows systems.  I have installed the Linux drivers which were downloaded from Sharp's website.  Everything appears to be fine, the printers are configured and look like they are working, they show the correct model number, IP and port information, etc.  

However, when I print something, even though Ubuntu says it printed and doesn't show any problems, nothing ever comes out the other end on any of these three printers, and there is no record on any of the printers themselves that anything was ever sent to them.  I can ping them fine from the Ubuntu box, and they are all configured with the appropriate trays, memory capacity, etc.  Anyone know what the problem might be?

---

### Post by ViperChief on 2009-08-11
Not real good with network printers. I've just started using my first one. I was amazed when it worked with Linux over a wireless network. Great Success!

My first step, if I were you, would be to look at the CUPS page. Open up a browser and enter the address localhost:631 From there, you can see your printers, jobs, etc....Hopefully that'll get you started or someone who knows more about printing will come help you out.

---

### Post by outerheaven11 on 2009-08-11
Thanks, I didn't know about that.  I gave that a try and from the configuration screen everything looks good.  The printers are shared and published and indicate they are online.  I just can't figure out why nothing is coming out the other end.

---

### Post by cariboo on 2009-08-11
Check to see if any jobs are being held in the queue. If they are, on the jobs page there should be a start printer button. I had the same problem with my HP laserjet 5P after restarting my server.

---

### Post by outerheaven11 on 2009-08-11
No jobs stuck in the queue, and everything seems to flow normally when doing the print job.  When I print the job it enters the queue for a bit, then disappears and shows up in the Completed Jobs section.  Nothing else happens, and nothing comes out of any of the printers.  Is there a print log file somewhere I can get a detailed report of the print job as it goes through the system?

EDIT:  I forgot to mention, in case it matters, that this machine is running in a virtual machine.  However I also have two other Windows-based VMs running on the same machine and have had no printing problems.

---

### Post by Itg on 2010-08-09
I have this exact same problem with the mx350n on my network. My next stop today will be to check if Sharp has a forum I can look over. While I'm here though, did you ever manage to get it to work?

---

