---
title: "setup wireless g ACX111 chipset (safecom) in dapper - no wrapper"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by gannic on 2006-08-05
This may not be much help, but I am new to ubuntu dapper (2 days) and got lost in the shell scripting completely. I found this [http://www.psychocats.net/ubuntu/permissions.php](http://www.psychocats.net/ubuntu/permissions.php)
That showed me how to use the GUI to edit, copy and paste system files.
Then this comment here to the make Ubuntu use the correct drivers.

The upshot....

"press Alt-F2 and type gksudo nautilus" 
to bring up the file browser with full permissions.
Then using the interface opened above...
"add
options acx firmware_ver=1.2.1.34
somewhere (anywhere) in /etc/modprobe.d"

--The correct firmware was built in to my release of Ubuntu dapper, but by default it was using the wrong one. You may want to check you have this version in the filesystem lib/firmware/..amd64../acx folder

Then reboot - it was as simple as that, no command line work, no compiling - which is lucky as I havent a clue.

To set up WEP just use the System > Administration > Networking tool. I'll be back to post about WPA if I get it working.
 
I had read posts that were up to 5 pages of assorted commandline shinnagins to do the same thing. Thanks to gmilon (for the option edit) and the other person ([http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)) who didnt leave a name.

I may stick with ubuntu now I dont have to reboot windows every time I want to use the internet.

---

### Post by UnixAnt on 2006-08-06
Yes that was a great help actually :D 

Under Breezy I simply used the Netgear WG511T firmware and my US Robotics 5410 card worked without a problem.  With Dapper, however, I have been scratching my head somewhat and just assumed the upgrade broke my wireless somehow.

Anyway - if you manage to get WPA up and running, please post it here as I would be interested in that myself.

Good work - thanks again for the info.

---

### Post by northforkriver on 2006-08-15
I was having the same problem, apparently.  Thanks! That worked great.

---

### Post by Flumuxed on 2006-09-22
Having spent an entire weekend trying to get my Safecom PCI wireless card working, a week later I found this post and it worked first time.  The person who wrote the instructions for this post is an absolute star - THANKYOU:D !!

---

### Post by Flumuxed on 2006-09-27
Can anybody confirm whether this solution will also work for Kubuntu?

---

### Post by Matt Houston on 2006-10-14
Excuse my ignorance, but when you say "add option acx firmware_ver=1.2.1.34 somewhere (anywhere) etc/modprobe.d" do you mean make a new text file (this folder is full of text files) and actually type "acx firmware_ver=1.2.1.34"? What do you call the text file, or do you type it in an exisitng text file?

---

### Post by rebird242 on 2006-10-14
That seemed to work for me BUT I cant seem to connect to my network. I tries and fails.

---

