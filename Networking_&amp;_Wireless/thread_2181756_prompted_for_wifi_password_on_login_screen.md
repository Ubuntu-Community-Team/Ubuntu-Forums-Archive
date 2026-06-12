---
title: "prompted for wifi password on login screen"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by gamblor01 on 2013-10-18
I recently started a new job and connecting to the wifi network works fine -- after I have logged in as my user.  It's not a huge deal, but when I first boot up the system gives me this huge message dialog stating "Authentication required by Wi-Fi network":

[ATTACH=CONFIG]247042[/ATTACH]



It's not a huge deal as I can just cancel out of the dialog, login, and within about 20-30 seconds it will eventually connect to my wifi network without anything further interaction (I already typed and stored my password previously).


If I enter my password and hit connect then it gives me another dialog asking about a certificate.  If I dismiss that dialog, then it "thinks" for a seconds and just displays the above dialog again.  Clicking on the certificate option just seemed to send it off into an infinite loop or something.  It never displayed any further dialogs but it never connected to wifi either.

Does anyone know what's up with this?  It's not hindering me in any way but it is a bit annoying...

---

### Post by praseodym on 2013-10-19
Please show:
```

cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by grahammechanical on 2013-10-19
What password are you entering? Is it your user password or the passphrase/wireless/encryption key that is needed to connect to the wireless access point/router? To speed up the OS loading process Ubuntu starts to make network connections before we reach the login screen. You may want to use Edit Connections or System Settings>Network to see if there is an extra connection to that access point that is not storing the authentication passphrase or wireless key. It could be that another wireless access point is in range and Ubuntu is offering to connect to that access point.

Regards.

---

### Post by kostkon on 2013-10-19
Are you sure you haven't enabled the *Available to all users* option in the settings for that wifi connection? If it is enabled then the connection is system wide and ubuntu tries to connect to the wifi network during boot and for some reason in your case it cannot find the password or you haven't set one. Either set a password or disable the aforementioned option.

Hope that helps.

---

### Post by gamblor01 on 2013-10-19
> **kostkon said:**
> Are you sure you haven't enabled the *Available to all users* option in the settings for that wifi connection? If it is enabled then the connection is system wide and ubuntu tries to connect to the wifi network during boot and for some reason in your case it cannot find the password or you haven't set one. Either set a password or disable the aforementioned option.

Hope that helps.
I checked and it is indeed set to be available for all users.  I only have my one user so that option really isn't necessary.  So you're suggesting I should disable it?  I'm not sure why it would matter because my password ***IS*** saved for the network.  Again, if I just dismiss the dialog and login then it will automatically connect to the network without any further invention on my part (because the password is already saved).

> **grahammechanical said:**
> What password are you entering? Is it your user password or the passphrase/wireless/encryption key that is needed to connect to the wireless access point/router? To speed up the OS loading process Ubuntu starts to make network connections before we reach the login screen. You may want to use Edit Connections or System Settings>Network to see if there is an extra connection to that access point that is not storing the authentication passphrase or wireless key. It could be that another wireless access point is in range and Ubuntu is offering to connect to that access point.

Regards.
I am entering my wifi password, not my account password.  It doesn't do anything when I enter it except bring up that other dialog about the how not using a certificate can lead to connecting to rogue networks or whatever.  We are not using a certificate so I just click ignore.  I checked in the network settings and there are only 2 wifi networks -- one for my office network and another for my home wifi.  Note that at home it connects before I even login -- without this weird message on the login screen.


Here is the crazy thing...it doesn't seem to have my password stored:

[ATTACH=CONFIG]247084[/ATTACH]



I'm not sure how this is possible since it connects automatically once I have logged in, which implies that the password is stored!  The crazy thing is that after entering the password, if I close the properties and then go into edit connections again...the password field is blank again.

I don't know what is going on.  I will see what happens when I get to work on Monday.  If it's still displaying this dialog then I will post the contents of the files that [COLOR=#000000]praseodym asked for[/COLOR].  I'm a little unsure why the password is stored, but seems to be blank every time I open that dialog.

---

### Post by gamblor01 on 2013-10-21
So it's still not automatically connecting, although editing my connection this time does actually seem to have a saved password value.  Here are the contents of the three files:

```

$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

---

### Post by sandbochang-o on 2014-01-17
Switching back from Windows to ubuntu I just encountered this funny thing,
the reason could be different, in my case because the connection requires a Certificate that is located in my home directory which is encrypted and not accessible prior to my logon.
So whenever it tries to connect at the start screen it attempts to ask me for a new password......not a big deal but very annoying.

A simple solution I found is to edit the connection, under general tab you can untick the "Allow all user to use this connection".
On doing so, it will no longer try to connect to that network on start screen, but after you have login it will still auto connect, hope it helps.

---

