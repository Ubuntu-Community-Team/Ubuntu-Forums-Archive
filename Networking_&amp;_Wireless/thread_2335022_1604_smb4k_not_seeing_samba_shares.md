---
title: "1604 smb4k not seeing samba shares"
date: 2016-08-24
forum: Networking &amp; Wireless
---

### Post by einhexenmeister on 2016-08-24
i have 3 kubuntu machines with previously installed 1404 lts versions

any smb4k network neighborhood lookups and subsequent mounts worked in 1404 flawlessly, regardless if with windows or smb linux shares

after a fresh install of 1604 i am able to see the shares and their content via dolphin

using smb4k, nothing shows up in the network neighborhood browser, except the workgroup name "WORKGROUP"

the only machines visible and accessible remain the windows based shares, none of the 3 kubntu 1604 machines show up

using the smb4k open mount dialog doesn't provide any working results, regardless of how i try to format the unc addr or ip address lines

to me it could be a compatibility issue with the new samba, since the windows shares work

it appears to be very very sad that such a basic function on a modern OS with gui support stopped working.

not being and expert, i still feel that i'm not doing anything wrong the way i try to use smb4k.

i can access all shares via dolphin and mount via the ancient command line in the 21st century, but the gui fails

one more point :

i can find the shares via network shares and their names and they will be listed

however, when i try to click "mount" i get

the url was passed is invalid
mounting the share ..... failed
mount error : could not resolve address for ....

this renders smb4k in conjunction with samba linux shares for any mount job completely useless

sadly, this is not the only issue i have with the new 1604 release

cheers

---

### Post by einhexenmeister on 2016-08-25
here is a fix that seems to work ... i tried it ... follow link to comment 11

[https://bugzilla.samba.org/show_bug.cgi?id=11841](https://bugzilla.samba.org/show_bug.cgi?id=11841)

client max protocol = SMB3
client ipc max protocol = NT1don't forget to restart samba with

sudo smbd reload

there was some talk that something in dolphin might no longer work ... don't know, but i tested the following

putting the share addr in the addr bar of dolphin still works

also another feature i was not aware is pretty cool

hit alt-f2 and an input dialog appears on top of your window ... now u can put the addr in there and a new dolphin window containing this addr appears ... cool

cheers

---

