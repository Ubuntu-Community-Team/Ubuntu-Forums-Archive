---
title: "Uninstall google earth"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by raequin on 2011-01-01
Running Ubuntu 10.04 I recently installed Google Earth by downloading and double-clicking "google-earth-stable_current_amd64.deb".  It does not work at all and I would like to uninstall it.  I've been unable to find help by searching so I'm turning to you.

None of the instructions on the eHow discussion ([http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html](http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html)) seem to help.  Google Earth seems to have installed in the /opt/google/earth/free/ directory.  Any suggestions?  Thanks,

---

### Post by gandaran on 2011-01-01
if you used a .deb package to install then open synaptic package manager or ubuntu software center and look for the google earth package, mark for complete removal and click the apply button.
note that if you installed google earth version 6 you need to install the 'lsb-core' package from the system package manager to run google earth, google earth wont work without this pacakge installed.

---

### Post by HazelIced on 2011-01-03
> **gandaran said:**
> if you used a .deb package to install then open synaptic package manager or ubuntu software center and look for the google earth package, mark for complete removal and click the apply button.
note that if you installed google earth version 6 you need to install the 'lsb-core' package from the system package manager to run google earth, google earth wont work without this pacakge installed.
THANK YOU!!!!!! THANK YOU THANK YOU THANK YOU!!!!!
I was stuck like 2 days looking for why it wouldn't run and a way to uninstall it. Guess I was over-thinking it all and never thought on checking Synaptic. Thank you again Gandaran!

---

### Post by jcolyn on 2011-01-03
Once you un-install you can re-install by following the below instructions. This will install the current version.

If you want to install the latest current version of Googleearth follow  these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Make sure your internet connection is active then open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once  the above process is completed close the terminal and go to your /home  folder where you will find a googleearth_xx.deb package. Double-click it  and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

---

### Post by raequin on 2011-01-04
Thanks everybody.

---

### Post by gandaran on 2011-01-04
> **jcolyn said:**
> Once you un-install you can re-install by following the below instructions. This will install the current version.

If you want to install the latest current version of Googleearth follow  these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Make sure your internet connection is active then open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once  the above process is completed close the terminal and go to your /home  folder where you will find a googleearth_xx.deb package. Double-click it  and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy
why go through this process if you can download the .deb package from google now [http://www.google.com/intl/en/earth/download/ge/agree.html](http://www.google.com/intl/en/earth/download/ge/agree.html) and install with two clicks!

---

### Post by safir on 2012-10-17
> **gandaran said:**
> why go through this process if you can download the .deb package from google now [http://www.google.com/intl/en/earth/download/ge/agree.html](http://www.google.com/intl/en/earth/download/ge/agree.html) and install with two clicks!
I installed Google Earth by dowloading the .deb file from google and also by the google earth package method described above, either way the result is the same. Once you start google earth, the first welcome screen appears for a few seconds , then disappears and leaves a blank screen. Earlier I had installed the previous version of google earth which worked fine till a couple of weeks ago when it started to behave the same way. I have tried to uninstall and re-install but no luck.

---

### Post by CharlesA on 2012-10-17
Please create a new thread instead of resing one from a year and a half ago.

---

