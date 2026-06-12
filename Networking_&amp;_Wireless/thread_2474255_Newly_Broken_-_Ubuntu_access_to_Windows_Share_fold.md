---
title: "Newly Broken - Ubuntu access to Windows Share folders via Samba"
date: 2022-04-25
forum: Networking &amp; Wireless
---

### Post by boohyperad on 2022-04-25
After many years of accessing my Workstation Windows share folders, it has suddenly broken on my Ubuntu 20.04.4 LTS laptop.
 (I can still successfully access these shares on my other iOS & Windows machines)
Using Nautilus/File Manager i get error meassages....
- Directly connecting to a Share Folder....                                    
               ----------"Unable to access location. Failed to mount Windows share: Invalid argument"
- Directly connecting to that PC (and see ALL shared folders)...  
               ----------"Unable to access location. Failed to retrieve share list from server. Connection refused."
- Directly connecting to "Windows Network" 
               ----------"Unable to access location. Failed to retrieve share list from server. No such file or directory."

I assumed it's due to a recent update of either Ubuntu, Windows, or Samba. But that's a guess.
My firewall is inactive, & I have checked my Workgroup name is consistent. 

I have read other discussions on this forum, and attempted repairs about this error with no solution to date.... (hence the new thread  :^\   )
This includes......
- updating Windows & Ubuntu
- installing old version of Samba
- Editing smb.conf files to add....
          - Adding "client min/max protocol = SMB1, 2, and 3" in sequential attempts - 
- Editing /etc/hosts file to include Windows server address/name

Following the failure of all above attempts, I then purged Samba installation & reinstalled the current Samba release.... still broken.

I hope there's an easy fix forsomething that's been trouble-free for so long.
(I'd like to stick with Samba, rather than NFS, as all sharing software has been set up for this.)
PS: I am a coding/IT neophyte so please explain any suggestions as if I was your 4 year old child  ;)

thanks, Boo

---

### Post by boohyperad on 2022-04-27
[SOLVED]
Further scourering of previous threads on this topic found solution for me...
Thanks to "Morbius1" from thread...     [https://ubuntuforums.org/showthread.php?t=2435292](https://ubuntuforums.org/showthread.php?t=2435292)
Adding  ".local " after my PC host-name in file manager's location bar fixes issue for me (never had to do this in the past)
Thanks Mobius1  ;^)

--------------------------------------------------------

[COLOR=#000000]You can get that error message from trying to access from your file manager any server that has disabled smb1. It's becasue of a bug in a sub-componenet of gvfs.[/COLOR]

[COLOR=#000000]Access it this way in your file managers location bar:[/COLOR]
[COLOR=#000000]Code:
[COLOR=#417394]smb[/COLOR]://win10-host-name.local/share-name[/COLOR]
[COLOR=#000000]You have to specify the [/COLOR][COLOR=#417394]windows[/COLOR][COLOR=#000000] host name and share name explicitly. You can't use [/COLOR][COLOR=#417394]smb[/COLOR][COLOR=#000000]://win10-host-name.local by itself to see the list of shares.

---------------------------------------------------------[/COLOR]

---

