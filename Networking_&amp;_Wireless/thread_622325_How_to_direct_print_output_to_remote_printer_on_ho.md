---
title: "How to direct print output to remote printer on home LAN"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by hca on 2007-11-24
On my home LAN running 3 Ubuntu 7,10 computers I am able to have a test print performed on a printer connected to a remote computer on the LAN. How can I have output from some application printed on the remote printer? The Print Menu (or Ctrl+P) does not seem to give any option for selecting printer - only the local printer can be used from the application.

---

### Post by gadgetgirl02 on 2007-11-24
Hi there:

The first thing you need to do is share the remote printer, so that other computers on your LAN can see it.

How to do this (assuming both systems are running Ubuntu):
[LIST=1]
[*]Log in to the computer which has the printer attached to it.
[*]Go to System -> Administration -> Printing and click on the word "Server" in the left-hand list.
[*]Make sure the following item is checked off: Share published printers connected to this system
[*]Click on the name of the printer you want to share in the left-hand list and go to the Policies tab.
[*]Make sure "Enabled", "Accepting Jobs", and "Shared" are all checked off.
[*]Go to the Access Control tab
[*]Make sure "Allow printing for everyone except these users" is selected (if you leave it blank, anyone who can get access thus far will be able to print).
[*]Now go to the remote machine(s), go to System -> Administration -> Printing, and add your printer (it will show up under one of the options -- I don't have my printer set up like this and don't have it memorised, but I don't remember getting stuck when I did have it configured like this -- sorry I'm not being more helpful here).
[*]Print a test page from the remote machine to make sure all is well.
[/LIST]

Hope this helps. Off to ask my own printer question...

---

### Post by hca on 2007-11-25
Thank you for the reply. I did all of the above before posting my question. Only in item 8 where the printer on the remote machine did nog show up. Trying to add the remote printer the machine goes searching.  A small window turns up with a picture of an electric light bulp and the text "searching". After some time i chose 'Internet Printing Protocol (ipp)' and entered IP-address of the machine with the printer connected (192.168.1.xxx) and confirmed adding it.
After that the application (Open Office) in its print menu gives me the possibility of selecting "Printing-Protocol" which seems to be a local name of the remote printer.

 It prints. It works. Thanks again!

---

