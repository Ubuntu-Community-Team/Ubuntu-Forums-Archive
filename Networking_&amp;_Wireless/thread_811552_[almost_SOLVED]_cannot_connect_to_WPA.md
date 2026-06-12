---
title: "[almost SOLVED] cannot connect to WPA"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by hades_6_6_6 on 2008-05-29
I'm using the ndiswrapper (package from the Hardy repository) to connect to my wlan (wpa) and it was running like a charm.
But at once it stopped to work (I think after I tried suspend). I still can see my router but I cannot connect anymore. I'm prompted for a password but it seems to be wrong. On the router log there is "Authentication failed".
Here is what I've already tried:
[LIST]
[*]deactivate wpa -> can connect, but it is not what I want.
[*]change wpa-passwd -> still cannot connect
[*]remove all profile from the nm-applet -> still cannot connect
[*]configure wpa-replicant manually -> still cannot connect
[*]re-install ndiswrapper from repository -> still cannot connect
[*]install WiCD instead of network-manager -> still cannot connect
[*]re-install network-manager instead of WiCD -> still cannot connect
[*]install newest ndiswrapper (1.53) manually instead of the repository one -> still cannot connect
[*]create a new ubuntu user -> works!!!:) the new user is able to connect, but my old user still doesn't:confused:
[/LIST]
So I guess there is something wrong with my $HOME (keyring?).
Do you have an idea which file/dir I could try to remove?

---

### Post by Aearenda on 2008-05-29
You could check the permissions on .gnome2/keyrings/login.keyring ```
ls -l .gnome2/keyrings/login.keyring
```Mine shows ```
-rw------- 1 aea aea 3975 2008-05-29 09:40 .gnome2/keyrings/login.keyring
```

Also go into System->Preferences->Encryption and Keyrings and make sure the login keyring's password matches your logon password.

---

