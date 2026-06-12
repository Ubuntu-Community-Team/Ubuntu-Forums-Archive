---
title: "cannot connect to windows share"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by sternkanz on 2008-01-08
Hi, I'm running Gutsy on a laptop and my friend is running Windows XP SP2 on his laptop. We want to set up sharing so that we can exchange files.

I've tried this with my own Windows machine and connecting to the Windows machine from Gutsy worked easily. However when I try to connect to my friends machine (by double-clicking on it in the Network view) I'm presented with a login popup which asks me for username, workgroup, and password. I can't seem to get further than this. Anything I put in doesn't work. I hit 'enter' and after a second the same popup comes up again.

If I click cancel it says:

'The folder contents could not be displayed.

Sorry, couldn't display all the contents
of "Windows Network: havoc".'

I've tried everything for the password, including my root login, my friends administrator login, and our own normal logins. Nothing works at all.

If anyone knows something we can do to make this works, please let me know!

Thanks!

Stern

---

### Post by reckless2k2 on 2008-01-08
well make sure that the windows firewall or whatever firewall he's using has file and printer sharing enabled. also, you log into his pc to his share with his username and password.

---

### Post by andguent on 2008-01-08
Also, on XP, check and see if "Simple File Sharing" is enabled or not. If it is enabled, then XP will only allow the guest account in.

To find:
* Open My Computer (or any other file browser window)
* Tools - > Folder Options
* Under the view tab, scroll ALLLLLL the way to the bottom

If changing that doesn't affect anything, try right clicking on his share and confirming share permissions. If it is XP Pro, the files themselves may have permissions listed under "Security" when right clicking the directory.

---

