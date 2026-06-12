---
title: "I need help working with Java Class files."
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Arazu on 2011-02-06
I just need to take a look at the code and in rare cases make a slight change and recompile it.

I tried the JadClipse plugin for Eclipse and the key part of the lengthy error message was this:
```
!MESSAGE Unable to create editor ID net.sf.jadclipse.JadclipseClassFileEditor: The Class File Viewer cannot handle the given input ('org.eclipse.ui.ide.FileStoreEditorInput').
```

Next I tried running jad by itself. The error is:
```
jad: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

I can't find those libraries in the repository. Based on what I see in Synaptic it would seem they are out of date.


So. What should I be doing here? I'd love to have this working in Eclipse but I'll settle for anything. I greatly appreciate any help you all can offer.

Thanks.

---

### Post by YesWeCan on 2011-02-09
Hi. I don't know for certain what the cause of this is. However, I recommend you do not use any repository Java nor OpenJava. Remove it all and download JRE and JDK from the Oracle site. This way you will be up to date.

---

### Post by lykeion on 2011-02-09
It's more likely an issue with plugin incompatibility with Eclipse. Checking JadClipse homepage I see it's not been updated to recent versions of Eclipse (current version is v3.5 and JadClipse is for v3.3). Use a decompiler that works with your Eclipse version, like [JD-Eclipse]("http://java.decompiler.free.fr/?q=jdeclipse").

@YesWeCan
Why do you recommend a totally irrelevant solution, again? I'm starting to think you are an Oracle employee or something ](*,)

---

