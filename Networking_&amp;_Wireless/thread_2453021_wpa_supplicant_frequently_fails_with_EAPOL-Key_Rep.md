---
title: "wpa_supplicant frequently fails with EAPOL-Key Replay Counter error on BCM43228"
date: 2020-11-01
forum: Networking &amp; Wireless
---

### Post by ajkessel on 2020-11-01
Running Ubuntu 20.04.1 LTS, linux 5.4.0-52-generic, on an older Dell Laptop with BCM43228 NIC. 

For several years, I had no problems, but recently the WiFi spontaneously drops out for several minutes at a time and then reappears. Toggling WiFi on/off sometimes helps but not always. Rebooting usually helps. The problem coincides with the log message  wlp2s0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet.

I've seen various forum postings in the past about this problem with older kernels but no clear solution, and nothing recent.

I tried switching from wpasupplicant to iwd, but iwd doesn't work at all -- I get these errors:

rfkill id 4 can't be matched to a wiphy
DEL_INTERFACE failed: Operation not supported
Could not register frame watch type 00d0: -95
message repeated 6 times: [ Could not register frame watch type 00d0: -95]
rfkill id 3 not found in a RFKILL_OP_CHANGE event

I've tried running wpa_supplicant with debug enabled; [a full log is posted here]("http://adam.rosi-kessel.org/bugs/ubuntu-wifi/2020-11-01-wpa-debug-log.txt").

Any ideas for how to fix/troubleshoot? Is this a NIC/driver problem or wpasupplicant problem? If the latter, is there a simple workaround to avoid using wpasupplicant?

---

