---
title: "dial up connection terminates immediately after connecting"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by jittopjose on 2007-10-14
i am using feisty and  pci modem (motorola sm56 speakerphone modem). after lots of search i found driver to this modem detected. but when i tried to connect , the connection droped immediately...some times its connects for 4 or 5 sec and get a few data...then again discunnected. i used gnome-ppp for dialling. but in windows this connection does not make any  problems..
i am here by attaching the terminal log what i got after running gnome-ppp with root privilage..


log 1
------

GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.56
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DP172222
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DP172222
GNOME PPP: STDERR: CONNECT 33333
GNOME PPP: STDERR: --> Carrier detected.  Waiting for prompt.
GNOME PPP: STDERR: Welcome to UTStarcom Total Control HiPer ARC (TM)
GNOME PPP: STDERR: Networks That Go The Distance (TM)
GNOME PPP: STDERR: login: 
GNOME PPP: STDERR: --> Looks like a login prompt.
GNOME PPP: STDERR: --> Sending: 4872354658
GNOME PPP: STDERR: 4872354658
GNOME PPP: STDERR: Password: 
GNOME PPP: STDERR: --> Looks like a password prompt.
GNOME PPP: STDERR: --> Sending: (password)
GNOME PPP: STDERR: ~[7f]}#@!}!}!} }?}!}$}%j}"}&[7f][7f][7f][7f]}%}&,\o<}'}"}(}"}1}$}%j}3}#} [05]V~
GNOME PPP: STDERR: --> PPP negotiation detected.
GNOME PPP: STDERR: --> Starting pppd at Sat Oct 13 14:22:36 2007
GNOME PPP: STDERR: --> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
GNOME PPP: STDERR: --> --> PAP (Password Authentication Protocol) may be flaky.
GNOME PPP: STDERR: --> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
GNOME PPP: STDERR: --> --> CHAP (Challenge Handshake) may be flaky.
GNOME PPP: STDERR: --> Pid of pppd: 6327
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> local  IP address 61.2.193.49
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> remote IP address 61.1.254.11
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> primary   DNS address 218.248.240.23
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> secondary DNS address 218.248.240.135
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> Terminating connection due to lack of activity.
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> Connect time 0.1 minutes.
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> pppd: H&#65533;&#65533;&#65533;0*[06][08]&#65533;[1b][06][08]

(gnome-ppp:6260): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> Disconnecting at Sat Oct 13 14:22:43 2007
GNOME PPP: STDERR: --> The PPP daemon has died: Link idle: Idle Seconds reached. (exit code = 12)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> I guess that's it for now, exiting
GNOME PPP: STDERR: --> The PPP daemon has died. (exit code = 12)






log 2 (this time it connected for a few sec)
-------------------------------------------------=


GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.56
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DP172222
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DP172222
GNOME PPP: STDERR: CONNECT 34667
GNOME PPP: STDERR: --> Carrier detected.  Starting PPP immediately.
GNOME PPP: STDERR: --> Starting pppd at Sat Oct 13 14:28:26 2007
GNOME PPP: STDERR: --> Pid of pppd: 6550
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> local  IP address 61.2.193.183
GNOME PPP: STDERR: --> remote IP address 61.1.254.11
GNOME PPP: STDERR: --> primary   DNS address 218.248.240.23
GNOME PPP: STDERR: --> secondary DNS address 218.248.240.135
GNOME PPP: STDERR: --> Terminating connection due to lack of activity.
GNOME PPP: STDERR: --> Connect time 0.1 minutes.
GNOME PPP: STDERR: --> Disconnecting at Sat Oct 13 14:28:30 2007
GNOME PPP: STDERR: --> The PPP daemon has died: Link idle: Idle Seconds reached. (exit code = 12)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> I guess that's it for now, exiting
GNOME PPP: STDERR: --> The PPP daemon has died. (exit code = 12)



plz help me if anybody know anything about it.
thanks
jittos....

---

### Post by jittopjose on 2007-10-15
anybody out there to help me?. it took almost one and half yrs of effort to get my modem detected. now it could not be connected.. plz help me...then only i can proceed to explore ubuntu..plz..
thanks

---

### Post by _duncan_ on 2007-10-15
Let's see if we can spot something with your gnome-ppp settings:

1. Launch gnome-ppp like you normally would.
2. Instead of connecting, click the "Setup" button.
3. A new window will open. Click on the "Options" tab.
4. Make sure the "Ignore terminal strings [stupid mode]" option is CHECKED.
5. Make sure the "Check carrier line" option is NOT checked.
6. Close the window and try connecting again.

These settings work well with smartlink modem chipsets. Not sure if they are applicable to your particular modem (motorola sm56).

Hang in there, my friend. Based on the connection log, I feel you are very close to getting this to work.

---

### Post by jittopjose on 2007-10-15
thank u my friend...
i tried many combinations in that option tab of gnome-ppp, but not exactly remembering whether i tried the combination that u said. any way let me try. i used to run gnome-ppp in sudo mode since i found some lines in log read "permission denied" .  i tried different data rate also...
now am supposed to try all the tools to connect...like wvdial, ppp, etc.... any how i have to get my modem worked under ubuntu...then only i can suggest ubuntu for my friends with full support from my part....
for me linux means ubuntu...
once again thank u for ur help....
jittos....

---

### Post by _duncan_ on 2007-10-16
You are welcome. Keep me posted on your progress. I have plenty of success working with the different connection tools (wvdial, KPPP, gnome-ppp and pppconfig) these past 2 years using Ubuntu.

---

### Post by jittopjose on 2007-10-16
i am away from my home for some time..i shall try that in this week end and definitely  post the result.. it may helpful to others also.
thanks
jittos....

---

### Post by jittopjose on 2007-10-21
hello friends...
now i could connect to net from my dial up connection.....gnome-ppp didnt work. i tried pppconfig.. it worked without any problem....  thank u for all  the support u all gave me
thanks
jittos....

---

### Post by Desigen on 2007-11-02
Thanks a lot, that was very helpfull.

---

