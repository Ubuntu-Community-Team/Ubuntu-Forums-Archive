---
title: "Problem with SSSD to join AD"
date: 2017-11-06
forum: Networking &amp; Wireless
---

### Post by eallegre on 2017-11-06
Hello
Recently i've been trying to join a windows active directory using sssd.

The configuration is okay and I can successfully reach the AD, request users and log in using these users. 
The problem is that when I reboot the computer, the SSSD service start, but it's doesn't work as intended. I can't reach the Active Directory anymore.

Running :
```
sudo systemctl restart sssd
```
seems to be fixing the problem but it's not very good since I need to sign into the local user, restart it, then sign out and then sign in using my AD account, it's very time consumming.

At first I tought it was a problem with AppArmor but it isn't, disabling AA then rebooting result in the same thing.

In the SSSD log I receive this error :
```
[sssd[nss]] [sss_dp_get_reply] (0x0010): The Data Provider returned an error [org.freedesktop.sssd.Error.DataProvider.Offline]
```

I can't seem to find what is the problem, any help would be appreciated, if you need additional information feel free to ask me.

---

### Post by eallegre on 2017-11-06
The solution was to tell the SSSD systemd file (/lib/systemd/system/sssd.service.d in my case) to start under specific conditions (network being online):

This was achieved by running the following commands:

```
mkdir -p /lib/systemd/system/sssd.service.d
echo '[Unit]
Wants=nss-user-lookup.target network-online.target
After=network-online.target' >> /lib/systemd/system/sssd.service.d/10-after-network.conf

```

I don't know why this isn't the default behavior of the service since it makes sense to be connected to the network before attempting to contact the Active Directory.

---

### Post by tmack8080 on 2017-11-07
Do you a have setup guide? I wasn't able to get this working using the Wiki article: [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

I'm able to join the domain but user authentication is not working.

---

