---
title: "Application suddenly stopped working (slicer3 with tcl/tk)"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by freak42 on 2010-07-10
My manually installed (64-bit) version 3.4 of Slicer ([http://slicer.org/](http://slicer.org/)) suddenly stopped to startup, after some investigation it exits with the following problem: 
> slicer Error: InitializeTcl failed

I have multiple versions of tcl and tk installed (8.3-8.5).

I cannot tell you what I might have done to break this application, I did issue a apt-get autoremove a while ago, this might have given the app some problems.

However I am stuck and do not know what to do. 

Any Ideas?


Btw: I found the likely part of the source code of the app that issues the error, if this is of any help to you:

from [http://www.na-mic.org/svn/Slicer3/trunk/Applications/GUI/Slicer3.cxx](http://www.na-mic.org/svn/Slicer3/trunk/Applications/GUI/Slicer3.cxx)

```
  
  // Initialize Tcl
  // -- create the interp
  // -- set up initial global variables
  // -- later in this function tcl scripts are executed 
  //    and some additional global variables are defined
  Tcl_Interp *interp = NULL;
  interp = vtkKWApplication::InitializeTcl(argc, argv, &cout);
  if (!interp)
    {
    slicerCerr("Error: InitializeTcl failed" << endl );
    return 1;
    }


```

many thanks in advance

---

