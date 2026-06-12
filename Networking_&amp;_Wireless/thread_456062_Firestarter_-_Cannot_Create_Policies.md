---
title: "Firestarter - Cannot Create Policies"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by comedian999 on 2007-05-27
I cannot create policies in Firestarter. The rule buttons in the policy tabs are deactivated (Greyed out), as are the Policy menu items.

I've tried manually starting Firestarter from the terminal using Sudo Firestarter and gksudo firestarter, as well as making the changes to the sudoers file to have Firestarter start without requiring the root password as described here: [http://ubuntuforums.org/showthread.php?t=409375](http://ubuntuforums.org/showthread.php?t=409375). No matter what I've tried, I can't get it to let me create or modify policies.

Could someone point me in the right direction? I'm about a week into using Ubuntu, and I'm sure I'm missing something dumb and obvious. :redface:

Thanks in advance for your advice.

---

### Post by comedian999 on 2007-05-27
> Could someone point me in the right direction? I'm about a week into using Ubuntu, and I'm sure I'm missing something dumb and obvious. 

And I was right.

By right-clicking in the Allow Connections From Host window in Firestarter's Policy tab, I got an activated Add Rule entry in the context menu that allowed me to add the rules I needed. 

Then by selecting Edit / Preferences / Interface / Policy, and checking on Apply Policy Changes Immediately and pressing Accept, the rules went into effect.

If you took a look at this to help out, thanks. :)

---

### Post by mmmsoap on 2007-10-21
.

---

### Post by mmmsoap on 2007-10-21
> By right-clicking in the Allow Connections From Host window in Firestarter's Policy tab, I got an activated Add Rule entry in the context menu that allowed me to add the rules I needed.

Just wanted to say thanks for the tip....The "Add Rule" button was normal when I was using firestarter with feisty. When I upgraded to Gutsy all of a sudden it was gray and I couldn't add rules anymore =(

Even after uninstalling and reinstalling firestarter, I got nowhere. The right-clicking thing worked, however, and now the rule buttons are back the way they should be.

Anyone have any idea why firestarter would break like that? (Not sure if firestarter was upgraded or not in the Gutsty upgrade, but if so, it gets installed broken....)

---

