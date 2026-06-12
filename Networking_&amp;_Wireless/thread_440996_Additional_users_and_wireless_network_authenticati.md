---
title: "Additional users and wireless network authentication"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by siloko on 2007-05-12
Hi,

I have just added a new user to my system (User B), having used just one login in the past (User X). User X was created during install and all my configuration has been done with User X logins, including setting up my WPA encrypted wireless network with networkmanager. When I login to my User X account network manager tries to bring up my wireless connection and to get the Network Key Keyring Manager prompts me for my password, and the authentication goes with out a hitch. Now if I login to User X first and then User B, User B has access to the internet. If I login to User B first (after a power down or reboot) I never get prompted for a password, networkmanager doesn't bring up an icon in the authentication area for me to manually enter the network key and I can't access any configuration programs/files because User B is not part of the 'sudo - ers' group. 

So how do I sort this? Is it just a case of adding User B to the sudo-ers group (presumably with Use Manager), although if User B wasn't me in disguise this would obviously have security implications . . . Is there another way to do it. I was hoping at least to get networkmanager to bring up an icon (I presume it has started in User B's account aswell) so I can manually enter my key . . .

Any thoughts would be appreciated

Cheers

---

### Post by spd106 on 2007-05-14
This is a strange issue you're having. I have set up multiple users who don't have sudo access and they can connect without any problems.

Perhaps check in System > Preferences > Sessions that Network Manger is enabled at start up.

---

### Post by siloko on 2007-05-15
Hi Thanks for your reply. There is no such directory tree in Xubuntu that I could find. The session Manager in XFCE gives only very rudimentary options (show suspend button etc), however I did find a solution to this problem. I added nm-applet to the AutoStart Applications config dialog and ensured that I didn't save my session. If I saved my session then I got multiple instances of the applet starting (this is a known bug according to launchpad). Perhaps there is a better way but this works for me :) I also reset my user - well added him then removed him from the sudo group which seemed to re-enable the prompt for the WPA network key, which I could then save on that users keyring. So now all is well.

I've responded also to the other thread you answered!!

---

### Post by irw on 2007-05-31
I have a slightly different variation on this.

network manager works fine for me, and if I then log on as another user, there is no problem for them. 
If another user logs on before me, they are prompted for the keyring password, but no password is accepted.

I have it set to automatically log on to NM to avoid entering two passwords.  
Previously this worked fine for other users, it is just over the last couple of weeks.  They do not have sudo or root access, nor do I want them to have it!

Any ideas why this may be / what I could do to cure it?

---

