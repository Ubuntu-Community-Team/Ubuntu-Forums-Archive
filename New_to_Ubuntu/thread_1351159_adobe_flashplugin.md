---
title: "adobe flashplugin"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by DarinB on 2009-12-10
what is the difference between adobe flashplugin installer 10.0.42 and adobe flashplugin 10.0.42?
i am on jaunty running firefox 3.015 i have adobe flashplugin 10.0.32... I received an update for adobe flashplugin 10.0.42 but it was grayed out. I tried unlocking firefox 3.015 but the update came in for the plugin installer 10.0.42 this caused the grayed out adobe flashplugin 10.0.42 to disappear? I am not sure which one is being used and what is the difference between the installer and the flashplugin? I heard that the next update on adobe flashplugin will be helpful on many issues with the choppiness of the video on hulu and youtube(I hope)

---

### Post by bswilson on 2009-12-10
Well, there's fundamentally no difference.  The adobe flashplugin installer is a package that has a compressed copy of the actual adobe software (*/usr/lib/flashplugin-installer/libflashplayer.so*).  The adobe flashplugin is how Mozilla identifies the plugin that runs in the context of Firefox.  

You can install the update to Karmic via apt-get, or you can use the installer package from the Adobe Web site.  Either way, you'll end up with the same Adobe code.  

Hope this helps.

---

### Post by DarinB on 2009-12-10
thanks that means i am running the latest flashplugin then. I think?

---

