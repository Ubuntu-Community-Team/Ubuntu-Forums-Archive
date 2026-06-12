---
title: "Lubuntu 16.04 on Acer Aspire One AOA 110-Ap netbook - atheros wifi fails on cold boot"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by alpage2 on 2016-05-23
The Atheros AR2425 wifi on this old netbook has always been very reliable with all previous versions of lubuntu, but after upgrading to lubuntu 16.04, it has a strange problem. On turning on the netbook from cold, the wifi never works - it is unable to see any network. Asking it to ping my router just gets a response of 'Network is unreachable'.

Rebooting (usually just once, but 2 or 3 times on rare occasions) gets the wifi working, and once this is acheived it is rock solid - no wifi problems until the next time it is turned on from cold.

I briefly considered whether this might be an intermittent problem indicative of an impending hardware failure - but I think not - its behaviour is very consistent, and a friend with the exact same model of netbook is experiencing exactly the same problem.

I downloaded and ran the wireless-info script - once after a reboot with the wifi working, and the following day after a cold boot, with the wifi not yet working. I then ran diff --suppress-common-lines on the two resultant wireless-info.txt files. The diff gave a large amount of output which I have looked through, but I'm afraid I don't know enough to recognise where the problem lies, and I would be grateful for advice on what it reveals.

I am uploading three files with this message - all compressed due to the file size limit of the forum: the output of the wireless-info script after a cold boot, and after a warm boot, and the output of running diff against these two output files.

Thanks in anticipation
Alan

---

