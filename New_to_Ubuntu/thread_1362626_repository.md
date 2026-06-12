---
title: "repository"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Greyhame on 2009-12-23
Can I set up openoffice.org as a repository? If so, how? What I really want is the openoffice suite that includes Base. I downloaded the installation package but PackageManager won't install it.

---

### Post by coffeecat on 2009-12-23
What package did you download and from where?

The package openoffice.org-base is in the Ubuntu repository. Simply mark it for installation in the Synaptic package manager or in Software Centre. You don't have to download anything. The package manager will do that for you automatically (it will download the package appropriate for your version of Ubuntu) and install it for you.

What versions of Ubuntu are you running?

---

### Post by Greyhame on 2009-12-23
I downloaded openofficesuite from openoffice.org.  I tried what you recommended, but there is no install button to push.  I am running Ubuntu9.1.

---

### Post by coffeecat on 2009-12-23
> **Greyhame said:**
>  I tried what you recommended, but there is no install button to push.

This is what you do. :)

Open System > Administration > Synaptic. Find the package openoffice.org-base in the middle pane. Right-click on it and click on 'Mark for installation'. It will probably then pop up another window saying 'Mark additional required changes?' and list three java-related packages. Click on the 'Mark' button. These are what are known as dependencies and what were probably preventing your downloaded package from being installed.

Once the 'mark additional' window has closed, you'll see that the 'Apply' button in the toolbar of the main Synaptic window is now green. Click on it and the necessary packages will be downloaded and installed for you.

The alternative method is to open Applications > Software Centre. Type 'openoffice.org-base' in the search field and highlight 'OpenOffice.org Database', click on the green arrow to the right..... I'll let you work out the rest. :wink:

**Edit:**

> **Greyhame said:**
>  I downloaded openofficesuite from openoffice.org. 

Do not use the downloaded package.

---

### Post by Greyhame on 2009-12-23
Got it.  Thanks a million.  I had to reload the packages.  The middle pane only showed installed packages.  Once I did the reload, I had a billion of them, and base was right there just like you said.  Thanks!

---

### Post by coffeecat on 2009-12-23
I'm glad it worked! The necessity for a reload was because the package metadata hadn't been refreshed since you installed. I'd assumed that had happened already automatically, but I'm glad you discovered it.

It's worth exploring both Software Centre and Synaptic. SC is easier to use; Synaptic is more powerful and flexible. Generally speaking, you don't need to download deb packages yourself. Most of what you need is in the repositories.

Happy Ubuntu-ing! :)

---

