---
title: "wine/itunes installation question"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by jsdieorksw on 2009-10-18
I'm trying to install itunes 8.0 with wine.  I'm using the instructions on winehq: 

4. open a text editor and paste the following text, save it as msipatch.txt in your wine folder

   From f4ce24960d26c69534e55b9e2e398480f63eae89 Mon Sep 17 00:00:00 2001
From: eric
Date: Sat, 6 Dec 2008 10:04:44 -0600
Subject: msi: hack for iTunes installer

---
 dlls/msi/action.c |    3 ++-
 1 files changed, 2 insertions(+), 1 deletions(-)

diff --git a/dlls/msi/action.c b/dlls/msi/action.c
index 5d9ba65..b7de7d6 100644
--- a/dlls/msi/action.c
+++ b/dlls/msi/action.c
@@ -872,7 +872,8 @@ static UINT ITERATE_Actions(MSIRECORD *row, LPVOID param)

     if (rc != ERROR_SUCCESS)
         ERR("Execution halted, action %s returned %i\n", debugstr_w(action), rc);
-
+    if( rc == 1603 )
+        rc = ERROR_SUCCESS;
     return rc;
 }

-- 
1.5.6.3

what folder does this go in?  I just installed wine and I'm not sure where this text file should go.

---

### Post by ikt on 2009-10-18
[http://jl.sg/2009/03/04/installing-itunes-8-under-wine-on-ubuntu-8-10-intrepid-ibex](http://jl.sg/2009/03/04/installing-itunes-8-under-wine-on-ubuntu-8-10-intrepid-ibex)

> 3. clone the wine git repository

git clone git://source.winehq.org/git/wine.git wine
cd wine



From what I can tell you are downloading the wine git repository to your local computer, so whichever folder you "cd wine" into is your wine folder.

If you're not using itunes for any itunes specific purpose another music organiser/player similar to itunes is songbird.

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

Hope this helps :)

---

### Post by deancasino on 2009-10-18
> **ikt said:**
> [http://jl.sg/2009/03/04/installing-itunes-8-under-wine-on-ubuntu-8-10-intrepid-ibex](http://jl.sg/2009/03/04/installing-itunes-8-under-wine-on-ubuntu-8-10-intrepid-ibex)



From what I can tell you are downloading the wine git repository to your local computer, so whichever folder you "cd wine" into is your wine folder.

If you're not using itunes for any itunes specific purpose another music organiser/player similar to itunes is songbird.

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

Hope this helps :)

I agree, Songbird is definitely taking over in this field. The interface is very simular to itunes too.

---

### Post by BikeHelmet on 2009-10-18
If you don't mind going with iTunes 7, [PlayOnLinux]("http://www.playonlinux.com/en/") has an install script for it, and can help you easily manage multiple Wine versions.

(Ignore me if you have some reason for wanting iTunes 8, or a reason for recompiling from scratch.)

---

### Post by jsdieorksw on 2009-10-22
Well I've used Songbird for a while but I've switched to kde and for some reason Songbird no longer recognizes my ipod so I would like to stay with songbird if I could get it to recognize my ipod.

---

### Post by murderslastcrow on 2009-10-22
I don't think the iPod plugin is included with the default install of Songbird any longer. You can always try Banshee, since it's very useful with the majority of iPods.

iTunes in Linux is always a hit and miss. And don't expect to sync very quickly even if you're lucky enough to get your iPod recognized. Unless you're planning to get songs from the iTunes store and strip the DRM, I can't imagine any practical use for iTunes either.

---

