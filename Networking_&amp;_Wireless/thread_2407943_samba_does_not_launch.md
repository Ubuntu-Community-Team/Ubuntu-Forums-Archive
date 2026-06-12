---
title: "samba does not launch"
date: 2018-12-11
forum: Networking &amp; Wireless
---

### Post by pjstock on 2018-12-11
over my years as a not very skilled Ubuntu user, one of the greatest challenges (and disappointments) I've found to Ubuntu has been how difficult it is to achieve the simple task of being able to see files on Ubuntu System A from Ubuntu System B, both my systems.
I've never been able to make networking and file sharing work.

having just done refresh installs of 18.04 on a desktop and a laptop, I thought now would be the perfect time to try again.

Step 1 appears to be installing (and I presume running) Samba.

From the Software Center I seem to have "installed" Sambe. but when I click on Launch, nothing seems to happen. Am I supposed to see something?

guidance anyone?

Or, if I am going down the wrong path to happy home file sharing, can you redirect me to a simpler approach? 

Peter

---

### Post by Morbius1 on 2018-12-11
> one of the greatest challenges (and disappointments) I've found to  Ubuntu has been how difficult it is to achieve the simple task of being  able to see files on Ubuntu System A from Ubuntu System B, both my  systems.I've never been able to make networking and file sharing work.
Because you have always done it the Windows way. You need to do it the Linux way. Ubuntu 18.04 and the version of samba it will install make it so discovery of each other is automatic. All you need to do is install samba on both machines:
```
sudo apt install samba
```
Even before creating any shares both 18.04 systems will "see" each other using the native Linux way of host discovery. No need for workgroups, netbios, etc....

[COLOR=#0000cd]**Note**[/COLOR]: When you went to the Software Center and installed "Samba" you installed system-config-samba not samba itself. If you feel you need to use it to create shares rather than using Nautilus you need to create a missing file:
```
sudo touch /etc/libuser.conf
```
Then run it this way:
```
sudo -H system-config-samba
```

---

### Post by pjstock on 2018-12-11
thank you.
FWIW, I don't think I ever got Windows file sharing to work either. shows my skill level I guess.)

But Yes, Indeed, I see that I do see my two systems under the "Other Locations" option.

I presume that I have to enable Sharing on any folders or locations I want to share. I have done that and, Yes, see those two locations remotely.

However, when I try to access either, I am prompted  for a User name, domain and Password. (trying to use Registered User option as Anonymous User doesn't connect either, even though I think I enabled sharing for Guest Access)

Trying my Login User name and password  for that Remote System (call it A), and leaving Domain as it is ("Workgroup") I get "Unable to Access LOcation.... Permission denied"

So, what are these User and Password? or where do I set them?

smbpasswd ??

(really? there is no GUI way to set up Samba users and passwords? I have to do it command line level? )

sudo smbpasswd -a <user_name> seems to have allowed me to set up a samba password

Now if I set that up on System B, does that allow System A to use that user and PW to access folders on System B? (I guess I will go upstairs and try and see what happens.)

Yes, it does. Success.
that's pretty Slick.
thank you. over and out.

---

