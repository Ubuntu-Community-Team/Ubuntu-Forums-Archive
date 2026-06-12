---
title: "How to get variables from ObexPushd"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Vadko on 2008-09-29
Hello,

Using 'obexpushd -B -s /user/local/bin/test' on Ubuntu enables me to receive files from bluetooth and send them to the a perl script or shell script 'test'.

Tried  a perl script with $file_content = <STDIN> in it but it doesnt work.
 
How can I make 'test' get the file or STDIN and store the MAC address and the content to variables and then delete the file or clear STDIN?

For example I need to do the following: 
- Send .vcs file via bluetooth and save the MAC address (00:00:00:00:00:00)to $mac_address 
- On the content find the '**keyword**' and save it to $found_word?

Content of file.vcs would be something like:
BEGIN:VCALENDAR
VERSION:1.0
BEGIN:VTODO
SUMMARY:**keyword**
DALARM:00000000T081000Z
AALARM:00000000T081000Z
CATEGORIES:MISCELLANEOUS
PRIORITY:2
STATUS:NEEDS ACTION
CLASS:PUBLIC
LAST-MODIFIED:20080708T013309Z
X-SONYERICSSON-DST:0
X-IRMC-LUID:00000001009E
END:VTODO
END:VCALENDAR 

Hope this is the right place to post this.

Regards,
V

---

