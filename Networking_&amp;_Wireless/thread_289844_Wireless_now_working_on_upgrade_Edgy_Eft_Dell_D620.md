---
title: "Wireless now working on upgrade Edgy Eft Dell D620"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by chaag on 2006-10-31
Here's a quick success story getting wireless working on my Dell D620 laptop ofter upgrading from Dapper to Edgy.

The scene:
Wireless was working fine on dapper. I used the instruction [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29") to build ndiswrapper from source.

After upgrade, wireless stopped working (of course)

Again following the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29") I grabbed the latest ndiswrapper stable build (currently 1.28) removed all traces of the old install and built ndiswrapper from source. All of the instruction in the HowTo work great.

At the end though, ifup wlan0 was not working.

Reaading dmesg output I saw:
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

This is troubling, 'cuase bcmw43xx is _NOT_ the driver we want as ndiswrapper users.

Something was getting int he way of using ndiswrapper and that something was bcmw43xx!!! Must have come with the (over?) helpful builders if edgy eft.

So, I find this article on [removing bcmw43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper?highlight=%28blacklist%29%7C%28bcm43xx%29")

Follow the steps at the top. ifdown/ifup wlan0 and whala! worky wireless

Hope that helps

---

