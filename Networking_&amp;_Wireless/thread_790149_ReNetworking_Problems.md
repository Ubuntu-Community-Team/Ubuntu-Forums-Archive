---
title: "Re:Networking Problems"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Shiv Prakash on 2008-05-11
Hi,

i am facing these weird problems in ubuntu 8.04.

My system is on a LAN comprising of about 18 computers(all Windows), of which 5 have internet connection which have been shared.
I recently shifted over from windows were the common habit was to just change my default gateway to the ip of the comp on LAN i want to take internet connection of and then just simply surf the net.

But ubuntu...well...the thing is 6 out of 10 times the system will automatically get the net connection with roaming mode enabled and then sometimes for no reason at all it refuses to. I then tried static ip addressing and gave a default gateway it didint work...then after few more tries static ip worked...i have tried a lot of variations with no consistency, generally roaming mode works.

I would really like to know

1. What roaming mode really does, how is it different from DHCP and IP
2. How to get my internet working because i dont face the above problems in windows

Also sometimes computers on LAN are accessible and then mostly not(ié through Places->Network)

Thanks for your help

PS i have just switched over from windows but access to internet is proving to be troublesome

---

### Post by chili555 on 2008-05-11
Roaming is part of Network Manager. [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)  It's very useful for computers that will be used at home, work, coffee shop, library and, moreover wired or wirelessly in any of these locations. The intent is for you to select the network you prefer, out of perhaps many, connect and surf. NM works perfectly for some and poorly for others; why, I don't know.

If this is not your situation, if this is a fixed work computer, then I'd uncheck roaming and put my connection details in System -> Administration -> Network. You could also uninstall NM, as some of us have.

---

### Post by Shiv Prakash on 2008-05-11
Yup NM was the reason i wasnt able to get around my static ip woes...uninstalled it and things now working in the internet department though LAN sharing still giving issues...

---

