---
title: "VPN start stop script"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by alanandhispc on 2007-02-13
Hi,

i have created 2 bash scripts that start and stop my vpn connection, the reason for this was that the pptp-gui utility wasn't adding the route to the connection (to a 10.2.0.0/24 network)

i have put these on the desktop and made them executable, but i can only run them through the terminal.

is there a way i can just double click on them to start the running of the script.

i take it assigning a gui based script execution to a .sh file might be a security risk, so i'll be more than happy to rename it to an un-used extension (ie: .alanvpn)

if theres a better way of doing this, please let me know.


Thanks


Alan

---

### Post by Jussi Kukkonen on 2007-02-13
Save the script in your home directory , or maybe ~/bin/ (so it won't fill your desktop). Then right-click on desktop, select "Create launcher", fill in name and the command (incl. path). Type should be "Application", unless you want to see the terminal output.

---

### Post by alanandhispc on 2007-02-13
thanks for your reply, i wil have a go at this tonight and let you know how i get on.


Thanks once again.


Alan

---

### Post by alanandhispc on 2007-02-13
Tested and working, thank you.

for anyone wondering how to do this step by step.

put your shell script somewhere; ie: the root of your home folder
right click on the desktop and select create launcher
click browse next to the command box and locate your script/command - add "gksudo " without quotes to the beginning of the command boxes contents if it needs to run with raised privileges.
give the launcher a understandable name: ie: work vpn on
click the "no icon" button if you want to add a icon
click ok

---

### Post by a5benwillis on 2007-02-13
How about a copy of those scripts!! I use the Cisco vpn client and have to run it in a terminal window. I wonder if this could be scripted? It does ask for a password during the process.

Ben

---

### Post by inko9nito on 2008-01-10
> **a5benwillis said:**
> How about a copy of those scripts!! I use the Cisco vpn client and have to run it in a terminal window. I wonder if this could be scripted? It does ask for a password during the process.

Ben

I second that. If it's not too much trouble, could you please post the scripts? :)

---

