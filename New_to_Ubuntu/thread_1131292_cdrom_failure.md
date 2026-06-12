---
title: "cdrom failure"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by crabclaw on 2009-04-20
Have tried just about everything to get this thing working and am at wits end.

Please find error message here: [http://pastebin.com/d656eb2db](http://pastebin.com/d656eb2db)

Every time the action fails I get a coaster. 8 & counting...

---

### Post by inobe on 2009-04-20
hi open application> accessories> terminal and type

```
dmesg | grep -i cd | grep -i rom
```

copy and paste the output on next post.

---

### Post by brunogirin on 2009-04-20
What version of Ubuntu are you using, what version of the brasero package and what CD writer? Do you have the ability to try with a different CD writer to check whether this is a hardware problem? Is it intermittent or does it happen every time?

Note: to get the version of the brasero package, you can type the following in a terminal:
```
sudo aptitude show brasero | grep -i version
```

Sorry about all the questions but the more we know, the better we can help you :-)

---

### Post by crabclaw on 2009-04-20
inobe: in answer to your question

```
[   28.063412] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.00 PQ: 0 ANSI: 5
[   28.207125] Uniform CD-ROM driver Revision: 3.20
[   28.207197] sr 0:0:1:0: Attached scsi CD-ROM sr0
[  148.588304] cdrom: This disc doesn't have any tracks I recognize!
[ 1508.559181] cdrom: This disc doesn't have any tracks I recognize!
[ 2418.870032] cdrom: This disc doesn't have any tracks I recognize!

```

---

### Post by crabclaw on 2009-04-20
brunogirin:

In answer to yours

Version: 0.8.1-0ubuntu2~hardy1

Am running Hardy. I burned ISO's before with a previous release on the same computer. Am burning a crunchbang ISO 698MB on a 700 record disc. I can't try another writer.

---

### Post by inobe on 2009-04-20
> **crabclaw said:**
> inobe: in answer to your question

```
[   28.063412] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.00 PQ: 0 ANSI: 5
[   28.207125] Uniform CD-ROM driver Revision: 3.20
[   28.207197] sr 0:0:1:0: Attached scsi CD-ROM sr0
[  148.588304] cdrom: This disc doesn't have any tracks I recognize!
[ 1508.559181] cdrom: This disc doesn't have any tracks I recognize!
[ 2418.870032] cdrom: This disc doesn't have any tracks I recognize!

```

that drive googled comes up with many issues, many have rma'ed the drive, it appears that it writes at a slower speed then what it's set at.

it could be a firmware issue, i have checked for bugs at launchpad and cdrecord was fixed last year, your model is even mentioned.

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/23203](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/23203)

edit: yes many issues [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225424)

---

### Post by crabclaw on 2009-04-20
Really sorry to be annoying about this but I don't really understand what they're saying. You couldn't give me a layman's piece of code I could copy & paste into terminal?

please. I'd be very grateful.

---

### Post by inobe on 2009-04-20
i think you will need to file a bug report at launchpad if you have updated the firmware and are sure that the dvd drive functions correctly.

considering it worked till hardy it's an obvious bug.

that's all the suggestion i have, i sure someone here may have more suggestions.

---

