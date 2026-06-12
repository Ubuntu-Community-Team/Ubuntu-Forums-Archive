---
title: "EasyH10 - Model template not found"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by KosmicheCam on 2009-01-23
I first posted this message on the EasyH10 forums, but due to inactivity my post hasn't been replied to there. Perhaps somebody on here could help?
=================================================

Hello all,

I am having a problem with easyh10 since upgrading from Ubuntu Hardy Heron 8.04 to Intrepid 8.10. I am getting the error message:

```
camandclaire@Hernando:~$ easyh10 -U -P
EasyH10 [CUI] 1.5  Copyright (c) 2005-2006 by Nyaochi

ERROR: H10 model template is not found.
```

This seems strange because I have a copy of the correct .model file (H10UMS_5GB_FW2.04-2.52.model) in the H10's root, labelled 'easyh10.model'.

Has anybody got an idea what could be going wrong? I have tried re-copying the model over, just to get the same error. Please help me update my database!

(By the way, I have an iriver H10 5GB UMS, firmware 2.53)

---

### Post by KosmicheCam on 2009-01-26
For others' information, I have solved my problem. I used the following command, which I suppose specified where the model file is located(?):

```
easyh10 -U -M /media/H10/
```

---

