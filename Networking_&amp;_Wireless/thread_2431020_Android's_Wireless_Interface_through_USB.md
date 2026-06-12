---
title: "Android's Wireless Interface through USB"
date: 2019-11-10
forum: Networking &amp; Wireless
---

### Post by watchyerbak on 2019-11-10
I am working on getting Android's wireless interfaces accesible to Ubuntu's Network Manager.
I cannot connect to the internet without using my Android. No ethernet and no Wifi card.
The interfaces are visible using ADB through USB but they are "Managed." How do I get to where I can use the android's wlan0 interface?

Updates to come...

Keywords: android Wifi Wi-fi wireless device interface USB driver

---

### Post by jetsam on 2019-11-10
This link may or may not be helpful; my guess is it will:
[How to use a smartphone as a mobile hotspot]("https://www.computerworld.com/article/2499772/how-to-use-a-smartphone-as-a-mobile-hotspot.html")

...I was recently given the above link myself when asking a similar question here.  I haven't followed through entirely yet, so I may not be much further help at the moment, but usually someone else can fill in the gaps...

Here's the most relevent section, from page two of the above link:
> *13. Can I use a third-party tethering app instead of the one that comes with the phone?*

> [B]Yes, there are several apps that let you set up a Wi-Fi hotspot. To the mobile data provider it looks like regular (not hotspot) data traffic. As a result, it doesn’t count towards your monthly hotspot data limit.

I don’t recommend any of these apps for iOS, as most are not available on the App Store and many require jailbreaking your iPhone. Third-party tethering apps are much easier to come by for Android. My current favorite is [PdaNet+]("https://play.google.com/store/apps/details?id=com.pdanet&hl=en_US"). It’s free and can be installed from the Google Play Store. It adds a very useful idle timer that shuts down the hotspot if nobody’s using it.   [/B]

Hope that helps.
--jetsam

---

### Post by jetsam on 2019-11-12
Can you install apps on your "Android?"  What device are you using?

Does the solution in this video work for you?  (More compatible but browser only)
[PdaNet+ with Linux]("https://www.youtube.com/watch?v=NqTw8M26-tk")

or this one, for lower level integration?  (System level)
[PDANet+ with Linux revisited]("https://www.youtube.com/watch?v=kP7kagBc_3k&feature=youtu.be")

---

