---
title: "LG dvd+-R mounting problem"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by minsf on 2009-01-25
I just bought LG DVD external DVD+-R.
"sudo mount -t iso9660 /dev/cdrom1 /media/cdrom1"
results in a "wrong fs" error. i cannot mount even with "-t autofs" ("please specify fs").
i can post the exact error messages upon request.
ideally, i will be able to burn a DVD iso file on it, and a few tar balls. in the meantime, even mounting a simple cd does not seem to work.
here's what lshw gives:
```
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GSA-E60L
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrom2
             logical name: /dev/cdrw1
             logical name: /dev/cdrw2
             logical name: /dev/dvd1
             logical name: /dev/dvd2
             logical name: /dev/dvdrw1
             logical name: /dev/dvdrw2
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 1.00
             serial: [HL-DT-STDVD-RAM GSA-E60L1.0007/05/15 7U02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
```
if you need more info let me know and i'll post here.
thanks

---

### Post by mc4man on 2009-01-25
Actually your lshw looks fine. Note that you have doubled up /dev links, that's normal for external usb cd/dvd drives.
For use with any apps your device is /dev/scd1 with the most used links of /dev/cdrom1, /dev/dvd1

As far as mounting you don't mount a device or media per se, just the file system. In the case of audio cd's and blank media there is nothing to mount, they are accessed at a location.

The actual location are
for audio cd's - home folder -> .gvfs/cdda mount on scdx
for blank media - burn:///

As far as music players how they access an audio cd depends on the player, some will default to /dev/cdrom and would need to be changed in it's settings. Others like vlc will use scdx and you set when opening.
Rhythmbox will look to .gvfs and if it finds a cdda mount will display it in 'devices'
If you want to ck., then insert an audio cd, navigate to home folder -> .gvfs/cdda... and see if the .wav's are there.

Burner apps usually work off of the drive itself, you pick it from a list and the app will ck. if writeable media is present. ( in your case DVD-RAM GSA-E60L

So I'd first ck. if an audio cd is available, insert one and navigate as mentioned above.

You should also give the drive an fstab entry if one isn't already. post this
```
cat /etc/fstab
```

If your not using 8.10 (intrepid) or 8.04 (hardy) please mention

---

### Post by minsf on 2009-01-27
md5man, 
i just wanted to say this is an excellent post that help me clarify some things and it also points me in interesting directions (i need to look into gvfs, etc).
as for the problem- i consider it as solved, since i was able to burn a CD. you were probably right when you said that since there is no file system there, there is nothing to mount. this encouraged me to just start burning and it worked. (though i still wonder why sometimes when i insert a blank cd it does NOT ask me if i want to burn something on it. however, most of the times it does)
bottom line- THANK YOU buddy- you post was great!

EDIT: by the way, i'm using 8.10

---

