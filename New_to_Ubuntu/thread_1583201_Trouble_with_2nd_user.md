---
title: "Trouble with 2nd user"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by johnqcooper on 2010-09-27
I've set up a single-boot system of Ubuntu 10.04. I've encountered no problems with my own user account. However, I've got network problems with my second account. Briefly put, the network manager applet in the notification area doesn't appear. 

The system is connected to the network, provided that I am also logged in to my own user account. If I log out of my own account and log in to the second account, there is no network access.

When I try to start Synaptic Package Manager on the second account, I'm prompted to enter my password. But when I enter my password and dismiss the dialog, nothing happens.

I created the second account as a Desktop user. Then I changed the type of account to Administrator. This had no effect on the problem.

I'd appreciate any light you can shed on this. Thanks!

---

### Post by johnqcooper on 2010-09-28
I've deleted the 2nd account and recreated it as an Administrator account from the get-go. In the main account, I've made sure that the wireless connection is available to all users. I can now access Synaptic on the 2nd account. When I'm logged into that account, it says that NetworkManager is installed. However, the NetworkManager applet still does not appear in the notification area. Nor is it available from Add to Panel.

Please help!

---

### Post by Paqman on 2010-09-28
Have you checked exactly what the second account has permission to do in Users and Groups? IIRC even an administrator account isn't set up to do everything by default.

---

### Post by johnqcooper on 2010-09-28
Yes, thanks for bringing that up. Although the option to use wireless networks is unchecked when you first create a new account (even if it's an administrator account), I made sure to check it.

---

