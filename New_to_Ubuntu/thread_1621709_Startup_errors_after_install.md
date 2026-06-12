---
title: "Startup errors after install"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by calz on 2010-11-14
I just installed ubuntu 10.10 a few days ago, and I just noticed that on startup I get a long list of errors just before the desktop loads. Everything seems to work fine, but I don't want something deeply hidden to spring up all of a sudden. What can I do?

---

### Post by apollothethird on 2010-11-14
> **calz said:**
> I just installed ubuntu 10.10 a few days ago, and I just noticed that on startup I get a long list of errors just before the desktop loads. Everything seems to work fine, but I don't want something deeply hidden to spring up all of a sudden. What can I do?

Not enough information.  Some of the messages you're looking at might be warnings or advisory messages.  Some of them might be error notices that you can ignore, such as a notice to tell you it's falling back to a different sound driver to appropriate match the sound card found.

What you might consider doing is working on one message at a time and getting familiar with what it's about and how you want to address it until you have it the way you want it.

I understand the situation about warning and error messages.  It's often like the system is crying wolf.  You don't want to get used to ignoring something that is an indication of some catastrophe about to happen, like a notice that your drive is failing and should be replaced soon.

Pick one of the messages with your followup and we'll be glad to help you with it.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Hippytaff on 2010-11-14
You can find a log of any boot errors by doing the following
```

cat /var/log/boot.log

```
If you post those details we will have a better idea of whats going on. There are other logs in /var/log/ folder which might be worth looking at too. Also
```

dmesg

```
will return startup info
:-)

---

### Post by calz on 2010-11-14
So this is what happened when I punched that code in:

fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 143951/3170304 files, 1159874/12675072 blocks (check in 3 mounts)
 * Starting AppArmor profiles                                                  
 Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Setting sensors limits                                                [ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
 * Checking battery state...   

Now the second code you gave me resulted in a ton of stuff that I don't think I should post it it's so long, but here it is:

[   16.123260] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.123263] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.123267] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   16.123273] end_request: I/O error, dev sdb, sector 8
[   16.125004] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.125006] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.125009] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.125012] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.125016] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   16.125022] end_request: I/O error, dev sdb, sector 24
[   16.126879] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.126881] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.126884] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.126887] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.126891] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   16.126897] end_request: I/O error, dev sdb, sector 24
[   16.128629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.128631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.128634] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.128636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.128640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   16.128647] end_request: I/O error, dev sdb, sector 56
[   16.129754] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.129757] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.129759] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.129762] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.129767] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   16.129773] end_request: I/O error, dev sdb, sector 56
[   16.137629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.137631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.137634] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.137637] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.137641] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   16.137648] end_request: I/O error, dev sdb, sector 120
[   16.139004] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.139006] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.139008] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.139011] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.139015] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   16.139022] end_request: I/O error, dev sdb, sector 120
[   16.140252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.140253] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.140255] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.140257] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.140260] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.140265] end_request: I/O error, dev sdb, sector 0
[   16.141265] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.141267] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.141271] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.141275] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.141280] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.141291] end_request: I/O error, dev sdb, sector 0
[   16.142380] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.142382] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.142385] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.142388] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.142392] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.142399] end_request: I/O error, dev sdb, sector 0
[   16.143504] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.143506] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.143509] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.143512] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.143517] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.143523] end_request: I/O error, dev sdb, sector 0
[   16.145129] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.145131] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.145134] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.145137] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.145141] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.145147] end_request: I/O error, dev sdb, sector 0
[   16.146879] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.146881] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.146883] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.146886] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.146890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.146897] end_request: I/O error, dev sdb, sector 0
[   16.148629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.148631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.148633] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.148636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.148640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.148647] end_request: I/O error, dev sdb, sector 16
[   16.150376] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.150377] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.150379] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.150381] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.150384] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.150388] end_request: I/O error, dev sdb, sector 128
[   16.152129] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.152131] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.152133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.152136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.152140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.152147] end_request: I/O error, dev sdb, sector 128
[   16.153878] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.153880] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.153883] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.153886] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.153890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.153896] end_request: I/O error, dev sdb, sector 128
[   16.155629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.155631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.155633] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.155636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.155640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.155647] end_request: I/O error, dev sdb, sector 16
[   16.156751] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.156753] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.156755] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.156757] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.156760] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.156764] end_request: I/O error, dev sdb, sector 128
[   16.157626] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.157628] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.157630] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.157632] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.157635] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.157639] end_request: I/O error, dev sdb, sector 64
[   16.158503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.158505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.158508] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.158511] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.158515] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.158521] end_request: I/O error, dev sdb, sector 64
[   16.159629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.159631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.159634] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.159637] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.159642] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.159648] end_request: I/O error, dev sdb, sector 64
[   16.160750] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.160752] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.160753] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.160755] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.160758] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.160763] end_request: I/O error, dev sdb, sector 64
[   16.162504] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.162506] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.162509] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.162512] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.162516] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.162523] end_request: I/O error, dev sdb, sector 64
[   16.164378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.164380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.164383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.164386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.164390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.164396] end_request: I/O error, dev sdb, sector 64
[   16.166128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.166130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.166133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.166136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.166140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.166146] end_request: I/O error, dev sdb, sector 64
[   16.167254] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.167256] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.167259] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.167262] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.167266] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.167272] end_request: I/O error, dev sdb, sector 64
[   16.168628] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.168630] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.168633] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.168636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.168640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.168646] end_request: I/O error, dev sdb, sector 64
[   16.170003] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.170005] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.170008] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.170012] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.170017] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.170028] end_request: I/O error, dev sdb, sector 64
[   16.171379] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.171381] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.171384] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.171387] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.171391] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   16.171398] end_request: I/O error, dev sdb, sector 256
[   16.172753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.172755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.172758] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.172761] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.172765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   16.172771] end_request: I/O error, dev sdb, sector 256
[   16.174128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.174130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.174133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.174136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.174140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   16.174146] end_request: I/O error, dev sdb, sector 264
[   16.175503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.175505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.175508] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.175511] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.175515] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   16.175521] end_request: I/O error, dev sdb, sector 264
[   16.176878] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.176880] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.176883] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.176886] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.176890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   16.176896] end_request: I/O error, dev sdb, sector 272
[   16.178253] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.178255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.178258] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.178261] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.178265] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   16.178271] end_request: I/O error, dev sdb, sector 272
[   16.179628] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.179630] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.179632] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.179635] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.179639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   16.179646] end_request: I/O error, dev sdb, sector 768
[   16.181003] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.181005] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.181007] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.181010] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.181014] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   16.181021] end_request: I/O error, dev sdb, sector 768
[   16.182378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.182380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.182383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.182386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.182390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   16.182396] end_request: I/O error, dev sdb, sector 776
[   16.183753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.183755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.183757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.183760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.183764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   16.183770] end_request: I/O error, dev sdb, sector 776
[   16.185128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.185130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.185132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.185135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.185139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   16.185146] end_request: I/O error, dev sdb, sector 784
[   16.186503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.186505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.186507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.186510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.186514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   16.186520] end_request: I/O error, dev sdb, sector 784
[   16.187878] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.187880] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.187882] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.187885] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.187889] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.187896] end_request: I/O error, dev sdb, sector 0
[   16.189252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.189254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.189257] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.189260] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.189264] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.189270] end_request: I/O error, dev sdb, sector 0
[   16.190627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.190629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.190632] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.190635] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.190639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.190645] end_request: I/O error, dev sdb, sector 0
[   16.192000] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.192001] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.192003] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.192005] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.192008] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.192012] end_request: I/O error, dev sdb, sector 0
[   16.193378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.193380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.193383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.193386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.193390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.193397] end_request: I/O error, dev sdb, sector 0
[   16.194753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.194755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.194757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.194760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.194764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.194771] end_request: I/O error, dev sdb, sector 16
[   16.196127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.196129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.196132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.196135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.196139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.196145] end_request: I/O error, dev sdb, sector 0
[   16.197503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.197505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.197507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.197510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.197515] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.197521] end_request: I/O error, dev sdb, sector 0
[   16.198625] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.198627] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.198629] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.198631] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.198634] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.198638] end_request: I/O error, dev sdb, sector 0
[   16.199502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.199504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.199507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.199510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.199514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.199521] end_request: I/O error, dev sdb, sector 0
[   16.200625] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.200627] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.200629] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.200631] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.200634] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.200638] end_request: I/O error, dev sdb, sector 0
[   16.201753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.201755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.201758] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.201761] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.201765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.201772] end_request: I/O error, dev sdb, sector 0
[   16.203502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.203504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.203507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.203510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.203514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.203520] end_request: I/O error, dev sdb, sector 0
[   16.205377] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.205379] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.205382] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.205385] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.205389] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.205395] end_request: I/O error, dev sdb, sector 0
[   16.207127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.207129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.207132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.207135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.207139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.207145] end_request: I/O error, dev sdb, sector 0
[   16.208253] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.208255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.208258] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.208261] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.208265] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.208271] end_request: I/O error, dev sdb, sector 0
[   16.209627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.209629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.209632] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.209635] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.209639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.209645] end_request: I/O error, dev sdb, sector 0
[   16.211127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.211129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.211132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.211135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.211139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.211146] end_request: I/O error, dev sdb, sector 0
[   16.212253] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.212255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.212258] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.212262] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.212266] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.212272] end_request: I/O error, dev sdb, sector 128
[   16.213128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.213130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.213133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.213136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.213140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.213147] end_request: I/O error, dev sdb, sector 128
[   16.214002] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.214004] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.214007] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.214010] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.214014] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.214020] end_request: I/O error, dev sdb, sector 16
[   16.214877] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.214879] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.214882] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.214885] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.214889] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.214895] end_request: I/O error, dev sdb, sector 0
[   16.215752] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.215754] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.215757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.215760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.215764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.215770] end_request: I/O error, dev sdb, sector 0
[   16.216627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.216629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.216631] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.216634] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.216638] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   16.216645] end_request: I/O error, dev sdb, sector 8
[   16.217502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.217504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.217506] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.217509] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.217513] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.217520] end_request: I/O error, dev sdb, sector 16
[   16.218377] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.218379] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.218381] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.218384] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.218388] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.218395] end_request: I/O error, dev sdb, sector 0
[   16.219252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.219254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.219256] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.219259] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.219263] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.219269] end_request: I/O error, dev sdb, sector 0
[   16.220125] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.220127] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.220130] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.220135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.220139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.220151] end_request: I/O error, dev sdb, sector 0
[   16.220999] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.221000] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.221002] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.221004] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.221007] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.221011] end_request: I/O error, dev sdb, sector 0
[   16.221877] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.221879] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.221881] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.221884] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.221888] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.221895] end_request: I/O error, dev sdb, sector 0
[   16.222752] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.222755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.222757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.222760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.222765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.222771] end_request: I/O error, dev sdb, sector 0
[   16.223627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.223629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.223631] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.223634] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.223638] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   16.223644] end_request: I/O error, dev sdb, sector 8
[   16.224502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.224504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.224506] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.224509] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.224513] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.224520] end_request: I/O error, dev sdb, sector 128
[   16.225376] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.225378] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.225381] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.225384] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.225388] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.225394] end_request: I/O error, dev sdb, sector 0
[   16.226252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.226254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.226256] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.226259] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.226263] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.226269] end_request: I/O error, dev sdb, sector 0
[   16.227127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.227129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.227131] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.227134] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.227138] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[   16.227144] end_request: I/O error, dev sdb, sector 4096
[   16.229378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.229380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.229383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.229386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.229390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.229397] end_request: I/O error, dev sdb, sector 0
[   16.230251] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.230252] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.230254] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.230256] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.230259] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.230263] end_request: I/O error, dev sdb, sector 0
[   16.231128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.231130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.231132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.231135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.231139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.231146] end_request: I/O error, dev sdb, sector 0
[   16.311468] ppdev: user-space parallel port driver
[   16.560780]   alloc irq_desc for 47 on node -1
[   16.560782]   alloc kstat_irqs on node -1
[   16.560790] fglrx_pci 0000:01:00.0: irq 47 for MSI/MSI-X
[   16.561142] [fglrx] Firegl kernel thread PID: 1307
[   16.561285] [fglrx] IRQ 47 Enabled
[   17.432308] [fglrx] Gart USWC size:1240 M.
[   17.432311] [fglrx] Gart cacheable size:491 M.
[   17.432314] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.432315] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   17.432317] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   18.759459] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   20.602810] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   21.346692] UDF-fs: Partition marked readonly; forcing readonly mount
[   21.347065] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/10/14 16:49 (1ed4)
[   22.451254] eth0: no IPv6 routers present
[ 1233.240011] usb 2-1: new high speed USB device using ehci_hcd and address 2
[ 1233.392179] scsi7 : usb-storage 2-1:1.0
[ 1234.390742] scsi 7:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
[ 1234.391133] sd 7:0:0:0: Attached scsi generic sg5 type 0
[ 1234.392108] sd 7:0:0:0: [sdc] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[ 1234.392748] sd 7:0:0:0: [sdc] Write Protect is off
[ 1234.392751] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1234.392754] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1234.394855] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1234.394859]  sdc: sdc1
[ 1234.665725] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1234.665729] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 1264.711508] usb 2-1: USB disconnect, address 2

Hopefully you can make something out here.

BTW I am new at this. Thanks for the help.

---

### Post by Hippytaff on 2010-11-14
:-)
For future reference - if you post any output you can highlight the text and click the # button to post it like this
```

[   16.123260] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.123263] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.123267] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   16.123273] end_request: I/O error, dev sdb, sector 8
[   16.125004] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.125006] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.125009] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.125012] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.125016] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   16.125022] end_request: I/O error, dev sdb, sector 24
[   16.126879] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.126881] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.126884] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.126887] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.126891] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   16.126897] end_request: I/O error, dev sdb, sector 24
[   16.128629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.128631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.128634] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.128636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.128640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   16.128647] end_request: I/O error, dev sdb, sector 56
[   16.129754] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.129757] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.129759] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.129762] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.129767] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[   16.129773] end_request: I/O error, dev sdb, sector 56
[   16.137629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.137631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.137634] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.137637] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.137641] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   16.137648] end_request: I/O error, dev sdb, sector 120
[   16.139004] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.139006] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.139008] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.139011] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.139015] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   16.139022] end_request: I/O error, dev sdb, sector 120
[   16.140252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.140253] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.140255] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.140257] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.140260] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.140265] end_request: I/O error, dev sdb, sector 0
[   16.141265] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.141267] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.141271] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.141275] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.141280] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.141291] end_request: I/O error, dev sdb, sector 0
[   16.142380] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.142382] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.142385] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.142388] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.142392] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.142399] end_request: I/O error, dev sdb, sector 0
[   16.143504] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.143506] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.143509] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.143512] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.143517] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.143523] end_request: I/O error, dev sdb, sector 0
[   16.145129] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.145131] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.145134] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.145137] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.145141] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.145147] end_request: I/O error, dev sdb, sector 0
[   16.146879] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.146881] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.146883] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.146886] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.146890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.146897] end_request: I/O error, dev sdb, sector 0
[   16.148629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.148631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.148633] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.148636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.148640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.148647] end_request: I/O error, dev sdb, sector 16
[   16.150376] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.150377] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.150379] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.150381] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.150384] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.150388] end_request: I/O error, dev sdb, sector 128
[   16.152129] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.152131] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.152133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.152136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.152140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.152147] end_request: I/O error, dev sdb, sector 128
[   16.153878] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.153880] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.153883] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.153886] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.153890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.153896] end_request: I/O error, dev sdb, sector 128
[   16.155629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.155631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.155633] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.155636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.155640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.155647] end_request: I/O error, dev sdb, sector 16
[   16.156751] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.156753] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.156755] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.156757] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.156760] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.156764] end_request: I/O error, dev sdb, sector 128
[   16.157626] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.157628] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.157630] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.157632] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.157635] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.157639] end_request: I/O error, dev sdb, sector 64
[   16.158503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.158505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.158508] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.158511] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.158515] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.158521] end_request: I/O error, dev sdb, sector 64
[   16.159629] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.159631] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.159634] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.159637] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.159642] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.159648] end_request: I/O error, dev sdb, sector 64
[   16.160750] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.160752] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.160753] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.160755] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.160758] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.160763] end_request: I/O error, dev sdb, sector 64
[   16.162504] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.162506] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.162509] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.162512] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.162516] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.162523] end_request: I/O error, dev sdb, sector 64
[   16.164378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.164380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.164383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.164386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.164390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.164396] end_request: I/O error, dev sdb, sector 64
[   16.166128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.166130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.166133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.166136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.166140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.166146] end_request: I/O error, dev sdb, sector 64
[   16.167254] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.167256] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.167259] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.167262] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.167266] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.167272] end_request: I/O error, dev sdb, sector 64
[   16.168628] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.168630] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.168633] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.168636] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.168640] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.168646] end_request: I/O error, dev sdb, sector 64
[   16.170003] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.170005] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.170008] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.170012] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.170017] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   16.170028] end_request: I/O error, dev sdb, sector 64
[   16.171379] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.171381] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.171384] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.171387] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.171391] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   16.171398] end_request: I/O error, dev sdb, sector 256
[   16.172753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.172755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.172758] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.172761] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.172765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   16.172771] end_request: I/O error, dev sdb, sector 256
[   16.174128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.174130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.174133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.174136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.174140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   16.174146] end_request: I/O error, dev sdb, sector 264
[   16.175503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.175505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.175508] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.175511] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.175515] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   16.175521] end_request: I/O error, dev sdb, sector 264
[   16.176878] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.176880] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.176883] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.176886] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.176890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   16.176896] end_request: I/O error, dev sdb, sector 272
[   16.178253] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.178255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.178258] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.178261] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.178265] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   16.178271] end_request: I/O error, dev sdb, sector 272
[   16.179628] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.179630] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.179632] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.179635] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.179639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   16.179646] end_request: I/O error, dev sdb, sector 768
[   16.181003] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.181005] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.181007] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.181010] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.181014] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   16.181021] end_request: I/O error, dev sdb, sector 768
[   16.182378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.182380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.182383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.182386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.182390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   16.182396] end_request: I/O error, dev sdb, sector 776
[   16.183753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.183755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.183757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.183760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.183764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   16.183770] end_request: I/O error, dev sdb, sector 776
[   16.185128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.185130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.185132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.185135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.185139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   16.185146] end_request: I/O error, dev sdb, sector 784
[   16.186503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.186505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.186507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.186510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.186514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   16.186520] end_request: I/O error, dev sdb, sector 784
[   16.187878] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.187880] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.187882] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.187885] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.187889] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.187896] end_request: I/O error, dev sdb, sector 0
[   16.189252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.189254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.189257] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.189260] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.189264] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.189270] end_request: I/O error, dev sdb, sector 0
[   16.190627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.190629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.190632] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.190635] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.190639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.190645] end_request: I/O error, dev sdb, sector 0
[   16.192000] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.192001] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.192003] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.192005] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.192008] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.192012] end_request: I/O error, dev sdb, sector 0
[   16.193378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.193380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.193383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.193386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.193390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.193397] end_request: I/O error, dev sdb, sector 0
[   16.194753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.194755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.194757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.194760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.194764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.194771] end_request: I/O error, dev sdb, sector 16
[   16.196127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.196129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.196132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.196135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.196139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.196145] end_request: I/O error, dev sdb, sector 0
[   16.197503] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.197505] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.197507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.197510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.197515] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.197521] end_request: I/O error, dev sdb, sector 0
[   16.198625] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.198627] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.198629] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.198631] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.198634] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.198638] end_request: I/O error, dev sdb, sector 0
[   16.199502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.199504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.199507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.199510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.199514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.199521] end_request: I/O error, dev sdb, sector 0
[   16.200625] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.200627] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.200629] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.200631] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.200634] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.200638] end_request: I/O error, dev sdb, sector 0
[   16.201753] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.201755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.201758] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.201761] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.201765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.201772] end_request: I/O error, dev sdb, sector 0
[   16.203502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.203504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.203507] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.203510] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.203514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.203520] end_request: I/O error, dev sdb, sector 0
[   16.205377] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.205379] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.205382] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.205385] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.205389] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.205395] end_request: I/O error, dev sdb, sector 0
[   16.207127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.207129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.207132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.207135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.207139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.207145] end_request: I/O error, dev sdb, sector 0
[   16.208253] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.208255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.208258] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.208261] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.208265] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.208271] end_request: I/O error, dev sdb, sector 0
[   16.209627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.209629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.209632] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.209635] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.209639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.209645] end_request: I/O error, dev sdb, sector 0
[   16.211127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.211129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.211132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.211135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.211139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.211146] end_request: I/O error, dev sdb, sector 0
[   16.212253] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.212255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.212258] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.212262] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.212266] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.212272] end_request: I/O error, dev sdb, sector 128
[   16.213128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.213130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.213133] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.213136] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.213140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.213147] end_request: I/O error, dev sdb, sector 128
[   16.214002] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.214004] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.214007] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.214010] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.214014] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.214020] end_request: I/O error, dev sdb, sector 16
[   16.214877] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.214879] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.214882] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.214885] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.214889] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.214895] end_request: I/O error, dev sdb, sector 0
[   16.215752] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.215754] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.215757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.215760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.215764] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.215770] end_request: I/O error, dev sdb, sector 0
[   16.216627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.216629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.216631] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.216634] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.216638] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   16.216645] end_request: I/O error, dev sdb, sector 8
[   16.217502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.217504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.217506] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.217509] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.217513] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   16.217520] end_request: I/O error, dev sdb, sector 16
[   16.218377] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.218379] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.218381] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.218384] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.218388] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.218395] end_request: I/O error, dev sdb, sector 0
[   16.219252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.219254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.219256] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.219259] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.219263] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.219269] end_request: I/O error, dev sdb, sector 0
[   16.220125] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.220127] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.220130] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.220135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.220139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.220151] end_request: I/O error, dev sdb, sector 0
[   16.220999] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.221000] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.221002] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.221004] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.221007] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.221011] end_request: I/O error, dev sdb, sector 0
[   16.221877] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.221879] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.221881] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.221884] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.221888] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.221895] end_request: I/O error, dev sdb, sector 0
[   16.222752] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.222755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.222757] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.222760] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.222765] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.222771] end_request: I/O error, dev sdb, sector 0
[   16.223627] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.223629] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.223631] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.223634] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.223638] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   16.223644] end_request: I/O error, dev sdb, sector 8
[   16.224502] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.224504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.224506] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.224509] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.224513] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   16.224520] end_request: I/O error, dev sdb, sector 128
[   16.225376] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.225378] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.225381] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.225384] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.225388] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.225394] end_request: I/O error, dev sdb, sector 0
[   16.226252] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.226254] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.226256] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.226259] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.226263] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.226269] end_request: I/O error, dev sdb, sector 0
[   16.227127] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.227129] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.227131] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.227134] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.227138] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[   16.227144] end_request: I/O error, dev sdb, sector 4096
[   16.229378] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.229380] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.229383] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.229386] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.229390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.229397] end_request: I/O error, dev sdb, sector 0
[   16.230251] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.230252] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.230254] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.230256] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.230259] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.230263] end_request: I/O error, dev sdb, sector 0
[   16.231128] sd 6:0:0:0: [sdb] Unhandled sense code
[   16.231130] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.231132] sd 6:0:0:0: [sdb] Sense Key : Data Protect [current] 
[   16.231135] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[   16.231139] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   16.231146] end_request: I/O error, dev sdb, sector 0
[   16.311468] ppdev: user-space parallel port driver
[   16.560780]   alloc irq_desc for 47 on node -1
[   16.560782]   alloc kstat_irqs on node -1
[   16.560790] fglrx_pci 0000:01:00.0: irq 47 for MSI/MSI-X
[   16.561142] [fglrx] Firegl kernel thread PID: 1307
[   16.561285] [fglrx] IRQ 47 Enabled
[   17.432308] [fglrx] Gart USWC size:1240 M.
[   17.432311] [fglrx] Gart cacheable size:491 M.
[   17.432314] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.432315] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   17.432317] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   18.759459] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   20.602810] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   21.346692] UDF-fs: Partition marked readonly; forcing readonly mount
[   21.347065] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/10/14 16:49 (1ed4)
[   22.451254] eth0: no IPv6 routers present
[ 1233.240011] usb 2-1: new high speed USB device using ehci_hcd and address 2
[ 1233.392179] scsi7 : usb-storage 2-1:1.0
[ 1234.390742] scsi 7:0:0:0: Direct-Access     Corsair  Flash Voyager    0.00 PQ: 0 ANSI: 2
[ 1234.391133] sd 7:0:0:0: Attached scsi generic sg5 type 0
[ 1234.392108] sd 7:0:0:0: [sdc] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[ 1234.392748] sd 7:0:0:0: [sdc] Write Protect is off
[ 1234.392751] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1234.392754] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1234.394855] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1234.394859]  sdc: sdc1
[ 1234.665725] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1234.665729] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 1264.711508] usb 2-1: USB disconnect, address 2

```easier to read (you can also type '[code] paste the output here [/code ]' - without the ' and the space after /code (I had to do the space so it didn't wrap the text :-)

---

### Post by apollothethird on 2010-11-14
> **calz said:**
> [ 16.123263] sd 6:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[ 16.123267] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[ 16.123273] end_request: I/O error, dev sdb, sector 8
[ 16.125004] sd 6:0:0:0: [sdb] Unhandled sense code
[ 16.125006] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE

It appears that your second hard drive is failing.  You probably should back up the data that is on that drive and replace it before it completely goes.

By the way, your OS appears to be installed on your first drive, so that one is safe.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by calz on 2010-11-15
Aha! That did it. I disconnected my external hard drive and the errors went away. Thanks for the help, I never would have known about that.

---

