---
title: "Cannot connect to wifi on server 22.04. No desktop installed"
date: 2022-07-03
forum: Networking &amp; Wireless
---

### Post by glenriver on 2022-07-03
Hello all.
I have a wifi network password that has a \ character in it like 1234\5678. Is this allowable when setting up my  wifi yaml file. Do the "" quotes like so "1234\5678" escape that character or do I need to change my network password?

thank you for any assistance

Update: When applying the netplan file I get error that the escape character \ is a problem. Will single quoted like '1234\5678' escape it. My new server setup is 22.04 and has been fully updated and no dekstop is installed. Maybe escape it like 1234/\5678. ?

Update 2: I tried doing this "1234/\5678" and still got complaint. So I changed to "1234\\5678" and no more complaint when generating and applying so Im thinking I escaped the \ character and yaml file is ok. Running sudo netpplan generate and sudo netplan apply generated no errors. I still do not have ip address for wifi when running ip a. I am very new to learning linux and since desktop versions do it all for you I decided to setup ubuntu server on an older available pc. I do not want a desktop on my server as I believe it will hender my learning.

Update 3: I removed the second character of \ in the password and instead went with this: so instead of "1234\\5678" I now have '1234\5678'. Running generate and apply did not result in any errers but still no ip address whrn running ip a even after reboot. I am lost and need help please.

---

### Post by glenriver on 2022-07-04
Single quotes did the trick

---

### Post by glenriver on 2022-07-04
single quotes

---

