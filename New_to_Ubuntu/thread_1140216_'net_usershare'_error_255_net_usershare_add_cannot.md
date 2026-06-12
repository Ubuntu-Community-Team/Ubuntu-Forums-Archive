---
title: "'net usershare' error 255: net usershare add: cannot convert name to SID"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by fl_spinach on 2009-04-27
Recently I ran into an error when trying to create a samba usershare using the GUI in Gnome, Ubuntu 8.04 upgraded to 8.10. I use winbind with active directory for authentication and am trying to give active directory users permissions to access the share.

'net usershare' returned error 255: net usershare add: connot convert name "Everyone" to a SID. Access denied.

When I tried it in the command line using the following statement

net usershare add <name of file for remote users> </local/path/to/file> <comments for remote users> <username>:F guest_ok=yes

I would get the same error 'net usershare' returned error 255: net usershare add: cannot convert name "<username>" to a SID. Access denied.

What worked for me was to lookup the SID with winbind:
wbinfo -n <username>
Which gives me the SID, a string in a format like
S-N-N-NN-NNNNNNNNNN-.....

If I then add the usershare using the SID in place of the username, like
net usershare add <name of file for remote users> </local/path/to/file> <comments for remote users> <S-N-N-NN-NNNNNNNNNN-....>:F guest_ok=yes

it works. So now I have two n00b1sh questions:
1) Is this a configuration error? Is there a way to make the net usershare add command use active directory to resolve the SID from a string?
2) Is there a convenient way to look up the SID for nonuser objects in Winbind, such as groups or computers? wbinfo -n only seems to work for users. Also, can permissions be granted to a machine's SID with user netshare add?

Thanks for any advice,

JS

---

### Post by sambajoe on 2011-12-28
Sorry for digging this old thread up, but I have exactly the same problem.
Any chance it was ever discovered what causes this behavior?

All Google results are littered with questions regarding a similar error, but only effecting guest access.
Namely the error is *[I]net usershare add*: *cannot convert name* "*Everyone*" to a *SID*. Invalid parameter.[/I] The cause seemed to be an error in the samba.conf, where no guest user account was defined.

But I have the same error as the OP. Trying to add a new usershare via:
```
net usershare add sharename /path/to/folder "Comment here" USERNAME:f guest_ok=n
```Results in: ```
net usershare add: cannot convert name "USERNAME" to a SID. NT_STATUS_INVALID_NETWORK_RESPONSE.
```Manually adding the usershare either by substituting the username with the SID *wbinfo -n* returns or by creating the appropriate files in /var/lib/samba/usershares works flawlessly.

So for some reason samba is not able to convert the username to a SID.. but I have no clue why and Googling for it only returns posts about the above mentioned unrelated error.

Strangely enough initially usershares worked fine for me. I used them for half a year, switched to global shares due to an unrelated problem and wanted to switch back now.

Any idea as to what could cause this behavior would be appreciated.

---

