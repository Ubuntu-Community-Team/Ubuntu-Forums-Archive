---
title: "How I Got WEP Shared Key To Work"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by rwoodsathome on 2007-07-12
After struggling through several nights googling and searching the Ubuntu forums for help I finally stumbled upon a set of commands that allowed my Belkin USG B wireless to connect to my DI-614+ router using WEP in shared mode.

Here is what I did.

sudo iwconfig eth2 key restriced
sudo iwconfig eth2 key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx

Then I clicked on the wireless icon to view the available wireless networks.
I clicked on the icon that causes the utility that accepts my shared key and stuff. I retyped the key (without the dashes (-)), selected shared mode, then connect.

Magic then happens and the keyring manager starts and wants a password for this connection. I just made up a password that had nothing to do with the shared key. Then I'm connected and working fine.

That's my story and I'm sticking to it.:guitar:

---

### Post by aysiu on 2007-07-12
I know it took you several nights to get WEP working, but isn't WPA more secure?

---

### Post by rwoodsathome on 2007-07-13
As I understand it WPA-PSK is more secure.

In my case I didn't want to have reconfigure all of the wireless devices in my household. And judging from the myriad of posts on 'how to get wep to work' I thought my experience could benefit someone who didn't want to change their entire  household.

---

### Post by aysiu on 2007-07-13
Cool.

---

### Post by kokobean on 2007-08-12
You are awesome! I've been battling this off and on for months. Only solution to work!
Thanks.

---

