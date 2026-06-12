---
title: "Unexpected way of messing up Network Manager"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by andrewkk on 2008-11-17
This intrigues me. I created a script that runs [gconftool --get and gconftool --recursive-list]("http://manpages.ubuntu.com/manpages/hardy/en/man1/gconftool-2.html") and added it as a startup program via my Gnome Session Preferences. Upon rebooting, strangely, nm-applet is nowhere to be found. When I disable the new startup entry and reboot again, nm-applet reappears. How is this measly script interfering with the Gnome Network Manager?

```
#!/bin/bash

keypath="/system/networking/wireless/networks/WWUwireless"

if [ "$(gconftool --get $keypath/essid)" = "WWUwireless" ]
then
	gconftool --recursive-list $keypath \
	| sed -e 's/ = /\n/g' -e 's/^ //g' \
	| zenity --list --title "Found wireless network configuration" --text "Would you like to remove this wireless network configuration?" --column "Key" --column "Value" \
	&& gconftool --recursive-unset $keypath
fi
```

---

