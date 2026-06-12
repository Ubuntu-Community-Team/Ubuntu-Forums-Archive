---
title: "kismet kismet_ui.conf file not in /etc/kismet"
date: 2019-03-27
forum: Networking &amp; Wireless
---

### Post by mark bower on 2019-03-27
I installed kismet via Synaptic Pkg Mgr, also via apt-get install.  I want to add to the display columns: 1)signal strength and 2)MAC addresses.  The /etc/kismet/kismet_ui.conf file is not present, and documentation says that is where these modifications are made.  The kismet.conf file is there and i modified the ncsource.

Ques1:  where do i go to make additions to the displayed columns?  Edit:  Please see my post #2

Ques2:  what is the difference between a network list versus a client list?

---

### Post by mark bower on 2019-03-28
I found the answer to Ques1.  I did not realize scrolling was involved to add additional columns to the list display.  So, the path for adding the dbm signal is, Kismet>Preferences>Network Columns>"scroll down" to Signal dbm>space bar & +/- to change to yes display or no display>tab to save and enter.

Synaptic loaded version 2013.03.R1b and I realized that kismet_ui.conf is no longer used.

---

