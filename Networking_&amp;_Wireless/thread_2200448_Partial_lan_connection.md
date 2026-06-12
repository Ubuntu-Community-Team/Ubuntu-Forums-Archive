---
title: "Partial lan connection"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2014-01-19
There are three Ubuntu computers on our lan: 2 X 12.04, 1 X 10.04 and one Win XP. Each computer can ping the other. 

Using Places/Network:

1) The 10.04 computer lists:

a) itself

b)Windows Networks (clicking on this shows MSHOME and Workgroup. Clicking on MSHOME, shows the Windows-only (i.e., no dual boot) computer on the network and I can log into it. Clicking on Workgroup shows the 10.04 computer [itself])

2) The first 12.04 computer (12.04-1) lists:
(for info: does not list itself)

a) the 10.04 computer

b) Windows Networks (clicking on this shows MSHOME and Workgroup:

-Clicking on MSHOME, shows the only Win computer [taking a long time to show]. This computer can sign into the Win computer.

-Clicking on Workgroup shows the 10.04 computer. Clicking on that and signing in shows the desktop of the 10.04. I can copy files from 10.04 to 12.04-1[this computer], but cannot write to 10.04)

3) The second 12.04 computer (12.04-2) lists: 

(does not list itself)

a) the 10.04 computer

b) Windows Networks (clicking on this shows MSHOME and Workgroup. 

-Clicking on MSHOME, shows the only Windows-only computer on the network [taking a long time to show] . This computer can sign into the Win computer and copy files from but cannot copy files to the Win

-Clicking on Workgroup shows the 10.04 computer. Clicking on that shows the desktop of the 10.04. I can copy files from 10.04 to 12.04-2[this computer], but cannot write to 10.04)

4) From inside WORKGROUP, the Win XP computer Network shows only the 10.04 computer, but not the two 12.04 computers

It appears that something needs to be enabled on the two 12.04 computers so that they are visible to each other, to the 10.04, and to the Win.

What information can I provide that will help determine the problem? (BTW, I may be just out of the newbie category, but maybe not. Please keep in mind as my experience is limited. Thanks.)

Update:

Have installed Samba again and there is improved visibility on both computers. But when I try to log into either from the other, I only see print$ and printers. I am assuming that I need to grant permission somehow to let my home folder be seen, but I cannot figure out how to do it. Maybe I am barking up the wrong tree?

Edit: It was the right tree. Permissions are controlled on Samba itself. Got all the permissions set for /home/user and all working correctly. Hope this might be helpful to someone else.

---

