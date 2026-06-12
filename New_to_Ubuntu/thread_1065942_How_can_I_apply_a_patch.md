---
title: "How can I apply a patch?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by null.byte on 2009-02-10
Hi. Can someone please tell me how can I apply a patch? For example here:

[http://bugs.winehq.org/show_bug.cgi?id=11747](http://bugs.winehq.org/show_bug.cgi?id=11747)

*            [EMAIL="focht@gmx.net"]Anastasius Focht[/EMAIL] *suggests using his patch, which can be found here: [http://bugs.winehq.org/attachment.cgi?id=11740](http://bugs.winehq.org/attachment.cgi?id=11740)

How can I apply that patch? How I must use it?

---

### Post by Hospadar on 2009-02-10
You'll need to download the wine source code, apply the patch, re-compile wine, re-install wine.
If this sounds like a pain in the a**, that's because it is. 
Should you still want to attempt it, first read up on how to compile things, how to apply diff patches to source code, how to compile wine correctly.  You'll first want to make sure you can compile wine correctly without any patches, then apply the patch, then compile.
Google can help with a lot of this.  None of these steps are particularly difficult, it can just be a pain to get everything working yourself.

If there is something you really need in wine that doesn't work, consider using a virtualized copy of windows, search for "virtual box" in the community docs in my sig.  They have a non-free (free as in speech) version which is free (as in beer) available from Sun, there's probably a link to it in the docs.  It's surprisingly easy to get a virtual machine up and running, and any machine pentium 4+ should be able to handle it just fine I'd think.

You'll need a windows installer cd for a virtual machine.  A cd-image (.iso) would work fine too.

---

### Post by null.byte on 2009-02-10
Thanks for your input. I'll try.

---

### Post by overlord.gaurav on 2009-02-10
First remove wine. Type this in a terminal:
```
 sudo apt-get remove wine 
```

Now, follow the following steps:

**[COLOR="Red"][NOTE: I've used the patch you mentioned in your post.][/COLOR]**
[B]
1. Open up a console and build the necessary wine dependencies[/B]
```

sudo apt-get install build-essential
sudo apt-get build-dep wine

```


**2.   Install git**
```

sudo apt-get install git-core gitk

```

**3. Clone the wine git repository**
```

git clone git://source.winehq.org/git/wine.git wine
cd wine 

```

**4. Open a text editor and paste the following text, save it as mypatch.txt in your wine folder  **

```
diff --git a/dlls/shdocvw/dochost.c b/dlls/shdocvw/dochost.c
index 908503c..c77463a 100644
--- a/dlls/shdocvw/dochost.c
+++ b/dlls/shdocvw/dochost.c
@@ -48,16 +48,11 @@ LRESULT process_dochost_task(DocHost *This, LPARAM lparam)

 static void navigate_complete(DocHost *This)
 {
-    IDispatch *disp = NULL;
     DISPPARAMS dispparams;
     VARIANTARG params[2];
     VARIANT url;
     HRESULT hres;

-    hres = IUnknown_QueryInterface(This->document, &IID_IDispatch, (void**)&disp);
-    if(FAILED(hres))
-        FIXME("Could not get IDispatch interface\n");
-
     dispparams.cArgs = 2;
     dispparams.cNamedArgs = 0;
     dispparams.rgdispidNamedArgs = NULL;
@@ -67,7 +62,7 @@ static void navigate_complete(DocHost *This)
     V_BYREF(params) = &url;

     V_VT(params+1) = VT_DISPATCH;
-    V_DISPATCH(params+1) = disp;
+    V_DISPATCH(params+1) = This->disp;

     V_VT(&url) = VT_BSTR;
     V_BSTR(&url) = SysAllocString(This->url);
@@ -76,8 +71,7 @@ static void navigate_complete(DocHost *This)
     call_sink(This->cps.wbe2, DISPID_DOCUMENTCOMPLETE, &dispparams);

     SysFreeString(V_BSTR(&url));
-    if(disp)
-        IDispatch_Release(disp);
+
     This->busy = VARIANT_FALSE;
 }



```

**5. Apply the patch to your wine source code**
```
git apply "mypatch.txt"
```
[B]
6. Compile the source code.[/B] (This takes a lot of time)
```
./configure && make depend && make
```
[B]
7. Install the modified version of wine[/B]
```
sudo make install
```

And now you're done with the installation!

---

### Post by null.byte on 2009-02-11
Thanks a lot for the time wasted to help me, overlord.guarav :) But I get an error when I try to apply the patch.
```

nullbyte@hwo:~/wine$ git apply "mypatch.txt"
fatal: corrupt patch at line 40
```

What's wrong?

---

### Post by overlord.gaurav on 2009-02-11
Something wrong with the patch you mentioned, I guess.

Edit: Okay, I figured it out.
I actually tried to patch wine, and I got the same error as you did.
Then I opened the file in gedit, and noted that there are only 39 lines, and it said that the 40th line was corrupted.
I added a few black lines in the ending of the patch and tried to patch it. TADA! It worked !

---

### Post by null.byte on 2009-02-11
nullbyte@hwo:~/wine$ git apply "mypatch.txt"
fatal: corrupt patch at line 21

:|

---

### Post by overlord.gaurav on 2009-02-11
Are you trying to apply any othe patches to wine too ?

And, try repeating the thing.
Navigate to your home folder. Delete the wine directory. Now go to the folder 'Source Code'. Copy the folder 'wine-1.x.x'. Get back to the home directory. Paste it there.
Rename it to wine.

Now create an empty text document.Rename the file to mypatch.txt. Paste the same code mentioned in my post. Save it. [without the blank lines in the ending]

Now go to a terminal and do:
```

cd wine
git apply mypatch.txt

```

You'll get a result which should look like:
```

overlord@overlord-desktop:~/wine$ git apply mypatch.txt
fatal: corrupt patch at line 40

```

Now, open the text file again. go to the last line. Hit an enter. Save the file.
Open the terminal, and do:
```

git apply mypatch.txt

```

Probably it should work.

NOTE: The file name need not be inside the iverted commas.

---

### Post by null.byte on 2009-02-12
I repeated it... now I get:
```

nullbyte@hwo:~/wine$ git apply mypatch.txt
error: patch failed: dlls/shdocvw/dochost.c:48
error: dlls/shdocvw/dochost.c: patch does not apply

```

---

### Post by overlord.gaurav on 2009-02-12
Which means there some patch already applied to it.
What I want you to do is: Delete the wine folder from your home directory and start from Step 1.
And after Step 4 is done: Hit enter at the end of the file and save it & repeat Step 4.

---

### Post by Lordeathman on 2010-11-28
Hey, I've been trying these steps for a while except with this patch: [http://bugs2.winehq.org/attachment.cgi?id=31413](http://bugs2.winehq.org/attachment.cgi?id=31413)

However, when I get to step 5 I get this:

k-leb@k-leb-desktop:~$ git apply '/home/k-leb/Desktop/falloutpatch.diff' 
error: dlls/d3d9/directx.c: No such file or directory

I know exactly where the directx.c file is and have navigated to it manually, as well as with ls: 

k-leb@k-leb-desktop:~$ ls wine/dlls/d3d9
buffer.c        d3d9.spec    query.c       swapchain.c  vertexdeclaration.c
cubetexture.c   device.c     shader.c      tests        volume.c
d3d9_main.c     directx.c    stateblock.c  texture.c    volumetexture.c
d3d9_private.h  Makefile.in  surface.c     version.rc
k-leb@k-leb-desktop:~$ ls wine/dlls/d3d9/directx.c
wine/dlls/d3d9/directx.c

EDIT. I'm now getting a different error:

k-leb@k-leb-desktop:~/wine$ git apply '/home/k-leb/Desktop/mypatch.txt' 
error: patch failed: dlls/d3d9/directx.c:474
error: dlls/d3d9/directx.c: patch does not apply

Any idea why the patch wouldn't apply?

---

