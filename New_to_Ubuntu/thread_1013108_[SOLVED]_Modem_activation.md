---
title: "[SOLVED] Modem activation"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by joepello on 2008-12-16
I am trying to set up my modem to dial in to my isp.  

First step is to get scanmodem.gz into my home directory.

I have scanmodem.gz on a CD but when I try to move it an error always pops up because it is owned by root.  I have tried changing permissions etc. to no avail.

---

### Post by achase79 on 2008-12-16
Copy to your hd as a superuser
In terminal
[code]sudo cp SOURCE DESTINATION[code]
after typing "sudo cp " you can drag the file from your other window into the terminal and it will automatically put in the path the destination would be your home folder in /home/username
since now you won't be on a ro disk you can change permissions with chown and chmod

---

