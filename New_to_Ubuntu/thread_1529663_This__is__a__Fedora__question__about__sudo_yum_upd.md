---
title: "This  is  a  Fedora  question  about  sudo yum updatde  command"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by jharp5 on 2010-07-12
I  am  having  a  problem  using  the  _sudo  yum  update_  command.  Everytime  this  commandline  prompt  is  entered  on  the  Fedora (RHEL)  linux  command  line , I  recieve  an  error  message  that  states  the  following :
 
_Cannot  retrieve  repository metadata (repmond.xml) for repository : fedora .  Please  verify  its  path  and  try  again._  
 
Could  someone  please  tell  me  what  I  am  doing  wrong and  what  I  can  do  to  correct  this  problem .

---

### Post by davidmohammed on 2010-07-12
I know this may sound daft - but surely you'll get a better and more accurate answer from a fedora forum? - ubuntu as I'm sure you're well aware uses a completely different packaging mechanism called debian...

---

### Post by RiceMonster on 2010-07-12
try doing this and then try again:
```
yum clean all
```

---

