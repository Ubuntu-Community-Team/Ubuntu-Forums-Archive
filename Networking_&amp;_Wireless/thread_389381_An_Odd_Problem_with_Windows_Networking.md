---
title: "An Odd Problem with Windows Networking"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by everchanging02 on 2007-03-20
I have been running Ubuntu on my laptop for the past six months, wanting to become more familiar with a Linux environment.  I started with 6.06, upgraded to 6.10 when it was released.  I've had no problems with connecting to my two windows desktops by use of Samba and the Network Servers link under Places.
However, this past week my hard drive crashed.  So I bought a replacement and reinstalled Ubuntu 6.10.  Now I cannot access my Windows PCs via Samba.  Using Places->Network Servers I can see the Windows Network, open my Network (named Galaxy), and see my computers (Terminus and Trantor), but when I try to open the computers (either one, trying trantor in this example) I get a message box after a long pause/loading:  "The folder contents could not be displayed.  Sorry, couldn't display all the contents of "Windows Network: trantor"."  I hit okay and it's just blank (as would be expected from not being able to load the files).
I haven't changed anything on my desktops in several months (as far as networking is concerned), so I am at a total loss as to why this is happening.
Any help with this would be greatly appreciated.  I need to make such a connection in order to retrieve the backed up data from the old hard drive.
Thanks.

- EC02

---

### Post by dmizer on 2007-03-20
it's a bug.  not sure which one, and i have no idea when it will get resolved.

in the mean time ... i suggest mounting your share with a line in your fstab file.  howto for that can be found in the second link in my sig.  please post in that thread if you have problems.

---

