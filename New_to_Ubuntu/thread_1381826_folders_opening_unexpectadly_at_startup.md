---
title: "folders opening unexpectadly at startup"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-15
for some reason when i have restarted my computer the last few times i have a couple of folders that open automatically once the desktop loads- i don't have them set to open in Startup Applications so i have know idea why they are opening on their own.

it started happening after i installed the latest version of frostwire (which crashed) with java and i had to restart the computer.

any ideas as to why this might be happening and how i can fix this?

---

### Post by sisco311 on 2010-01-17
> **Matt26 said:**
> for some reason when i have restarted my computer the last few times i have a couple of folders that open automatically once the desktop loads- i don't have them set to open in Startup Applications so i have know idea why they are opening on their own.

it started happening after i installed the latest version of frostwire (which crashed) with java and i had to restart the computer.

any ideas as to why this might be happening and how i can fix this?

go to System -> Preferences Startup Applications -> Options tab and deselect the Automatically remember running applications checkbox.

Open your file manager, press Ctrl+H to list hidden files, go to ~/.gnome2 and rename (or delete) the *session* file. In 9.10 (Karmic Koala) rename/remove the ~/.config/gnome-session/saved-sassion directory.

Log out and log back in.

---

### Post by Matt26 on 2010-01-21
> **sisco311 said:**
> go to System -> Preferences Startup Applications -> Options tab and deselect the Automatically remember running applications checkbox.

Open your file manager, press Ctrl+H to list hidden files, go to ~/.gnome2 and rename (or delete) the *session* file. In 9.10 (Karmic Koala) rename/remove the ~/.config/gnome-session/saved-sassion directory.

Log out and log back in.

thanks for the suggestion, but the check box under the Options tab of Startup applications is already unchecked.

is there anything else i can check?

---

