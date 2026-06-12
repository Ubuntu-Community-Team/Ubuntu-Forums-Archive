---
title: "lost websites min, max and close icons and top task bar"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by a.v.l on 2010-08-24
How do I reinstate the missing minimise, maximise and close icons on web pages please. I've also completely lost sight of the top task bar when a web page is opened. The task bar isn't set to auto hide. I've just discovered that this appears to be a Firefox thing as everything works normally in the Opera browser.

---

### Post by LiquidMeson on 2010-08-24
f11 ?

---

### Post by HeadHunter00 on 2010-08-24
Sorry, but I don't quiet follow what you mean. Can you give some more details to your problem.

---

### Post by LiquidMeson on 2010-08-24
might also be spam :(,  try restarting the computer. Hold down the power button for 10 seconds and then turn it back on.

---

### Post by MartyBuntu on 2010-08-24
> **LiquidMeson said:**
> might also be spam :(,  try restarting the computer. Hold down the power button for 10 seconds and then turn it back on.


^^^^^^^^
*Don't do this. A hard shutdown on a running system is not advisable unless there is no other alternative, like a freeze up.*


Do you have Compiz installed?

Look in **Applications > System Tools > Compiz Fusion Icon**
Click **Compiz Fusion Icon**...the icon will appear in your taskbar as a blue box with a white arrow in it. Right click the icon and select **Reload Window Manager**. This will reload the window manager.
Your problem seems common with some people using Compiz, including me. I know no other way of fixing this, other than this simple workaround for the time being.

Here's the command to install Compiz and icon in case you don't already have it.

**sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager**

---

### Post by the.phantom on 2010-08-24
> f11 ?

he was saying press the f11 key
it will toggel firefox to full screen
press it again and returns to normal

---

### Post by a.v.l on 2010-08-24
> **LiquidMeson said:**
> f11 ?

Thanks F11 brought back the task bar. The minimise, maximise and close (x) icons are still missing from all web pages in Firefox but not in Opera. There, they can be seen on the top left as normal in 10.04. Photos attached shows both browsers, which I hope demonstrates the problem.

---

### Post by MartyBuntu on 2010-08-24
Which version of Firefox do you have installed?

I had the same problem, but after my upgrade to Lucid, the problem never came up again.

---

### Post by a.v.l on 2010-08-24
> **MartyBuntu said:**
> Which version of Firefox do you have installed?

I had the same problem, but after my upgrade to Lucid, the problem never came up again.

Firefox 3.6.8 version, thanks.

---

### Post by LiquidMeson on 2010-08-24
Thanks for the pics, in ff, try holding down alt while clickn dragging the window.

I've seen this before but I forget how I solved it. Any updates available? System>admin>update manager

---

### Post by a.v.l on 2010-08-24
> **LiquidMeson said:**
> Thanks for the pics, in ff, try holding down alt while clickn dragging the window.

I've seen this before but I forget how I solved it. Any updates available? System>admin>update manager

Brilliant - holding down alt and dragging the firefox page pulled the top of the web page down, which was UNDER the top task bar, your a gem, thanks very much.

---

### Post by bgillard on 2011-01-04
I realize this is trivial, but:

In my case the **System Tools** menu was missing from the **Applications** menu. Right click on **Applications** and select **Edit Menus** to add or remove items. If the Compiz Fusion Icon still isn't there, follow the steps above.

---

