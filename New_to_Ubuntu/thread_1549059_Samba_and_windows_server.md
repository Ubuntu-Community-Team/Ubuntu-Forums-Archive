---
title: "Samba and windows server"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by jharp5 on 2010-08-09
I was  reading  the information under  the tips portion  of  the  ubuntu  forum when  I came  across  something  in the  samba  tutorial  that  caught  my  attention . According  to  the  tutorial  article ,  Samba  can be  used  to  establish  a  trust  with  windows  server  that  is  using  Windows NT .  I  was wondering  if  this  trust  with   a  domain could  affected  if  the  windows  server  that  is  linked  to  samba had  been  promoted   to  a  newer  version  of  windows  server  like  Windows 2008 or  Windows  2003 .  In  other  words , would  I  have  to  reestablish  a  connection  with  a  Windows  Server  if  I  decided  to upgrade  it  to a  newer version  of  windows  server OS ? If  this  makes  any  sense  please  respond  as  soon as  possible.:)

---

### Post by lukeiamyourfather on 2010-08-09
Winbind (part of Samba) can authenticate against Active Directory on multiple versions of Windows Server. Not sure about Windows Server 2008 though.

---

### Post by jharp5 on 2010-08-09
cool beans , i'll  keep  donig  some  research  on  the  matter thank ya  much

---

