---
title: "VB.Net app built on VS2010 possible on Ubuntu?"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by EccentricDyslexic on 2011-02-14
Hi all
 
I am new to Ubuntu and want a small program i wrote in vb to use on a Ubuntu laptop.
 
I have instaled Wine but cant seem to get the clickonce .application file to run or install.
 
Any ideas?  
 
Cheers!
 
Steve

---

### Post by Joeb454 on 2011-02-14
You may be able to run your application using [Mono](http://www.mono-project.com/) and [MonoDevelop](http://www.monodevelop.com), but there's no guarantees

---

### Post by directhex on 2011-02-14
You can't use ClickOnce files, and there's no support for .NET 4.0 YET in Ubuntu (it's coming)

A .NET 3.5 app should run with Mono.

---

### Post by EccentricDyslexic on 2011-02-14
Thanks for the info.
 
Ok so no go with the clickonce, can VS2010 publish into an .exe file and can that run on Wine?
 
Have downloaded monodevelop but cant seem to run my .sln files from with in that....
 
steve

---

### Post by shunan on 2011-02-14
Mono is the way, but if you want to use wine to run the compiled exe, you have to make it executable and just double click, and pray everything goes ok!

truth is success depends on a lot of things! so be more specific...

---

### Post by directhex on 2011-02-14
> **EccentricDyslexic said:**
> Ok so no go with the clickonce, can VS2010 publish into an .exe file and can that run on Wine?

No. Wine can only run Windows PE executables. VB.NET can only be compiled to a .NET assembly, which you run with Mono.

---

### Post by shunan on 2011-02-14
thanks for the clarification, i guess than EccentricDyslexic can try and import the project to monodevelop and compile...

thanks again.

---

### Post by directhex on 2011-02-14
> **shunan said:**
> thanks for the clarification, i guess than EccentricDyslexic can try and import the project to monodevelop and compile...

thanks again.

An executable (i.e. .exe file) compiled with Visual Studio.NET will run on Ubuntu. As long as it doesn't need .NET 4.0

It doesn't help clear things up when PE files (.exe) have the same extension as .NET assemblies (.exe) even though they're not even remotely the same thing.

---

### Post by EccentricDyslexic on 2011-02-15
Will need a bit of a walk through with this guys!
 
I have a vb.net app that i wrote with vs2010.  i have the .sln file and its associated folders.  If i publish it i get a clickonce file.  
 
I am not bothered about using Wine, i just want to run my program on a machine with Ubuntu.  
 
I have mono and monodevelop on my windows PC but cant make head nor tale of how to move forward...do i need them on the Ubuntu machine too? or maybe just mono?  if so how do i run my program with it?
 
Help! lol
 
Steve

---

### Post by directhex on 2011-02-15
> **EccentricDyslexic said:**
> Will need a bit of a walk through with this guys!
 
I have a vb.net app that i wrote with vs2010.  i have the .sln file and its associated folders.  If i publish it i get a clickonce file.  
 
I am not bothered about using Wine, i just want to run my program on a machine with Ubuntu.  
 
I have mono and monodevelop on my windows PC but cant make head nor tale of how to move forward...do i need them on the Ubuntu machine too? or maybe just mono?  if so how do i run my program with it?
 
Help! lol
 
Steve

A ClickOnce file is no use to you. You can't use it on Ubuntu.

Take the .exe files and .dll files produced by your solution, copy them to your Ubuntu system, and run "mono foo.exe"

Report back on any errors.

---

### Post by EccentricDyslexic on 2011-02-15
Ok i have published the program to my desktop and there is one .exe file but no .dll files...am i looking in the right place?
 
cheers
 
steve

---

### Post by EccentricDyslexic on 2011-02-15
Also strugling to find the download link for the mono ubuntu 10.10 combo....
 
edit- have found mono develop in software centre and have instaled that.  
 
Unsure how to do the- mono foo.exe thing....?
 
cant find mono foo or foo in software centre...
 
steve

---

### Post by directhex on 2011-02-15
.......

Click "Applications", "Accessories", "Terminal".

Type "cd Desktop"

Type "mono foo.exe" where foo.exe is the name of your assembly.

---

### Post by EccentricDyslexic on 2011-02-16
thanks for that...foo? not heard that one before! lol
 
ok done that, discovered it has to be typed in exactly the same...seems to be case sensitive.
 
my .exe is called "working example.exe" but when i type in mono working example.exe i get an error-
cannot open assembly "working":no such file or directory.
 
?
 
thanks for the help!
 
Steve

---

### Post by EccentricDyslexic on 2011-02-16
ok, renamed the exe to remove the space and retried- got this error-
** (workingexample.exe:1686): WARNING **: The following assembly
referenced from /home/steve/Desktop/workingexample.exe could not be
loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    10.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed
in the MONO_PATH environment variable, or in the location of the
executing assembly (/home/steve/Desktop/).


** (workingexample.exe:1686): WARNING **: Could not load file or
assembly 'Microsoft.VisualBasic, Version=10.0.0.0, Culture=neutral,
PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded
[steve@steve-Satellite-PRO-L10:~/Desktop$]("wlmailhtml:{D760F779-3316-4300-A3CD-9F88E66CC1E7}mid://00003472/!x-usc:mailto:steve@steve-Satellite-PRO-L10:~/Desktop$") 

Thanks again chaps!
 
Steve

---

### Post by directhex on 2011-02-16
> **EccentricDyslexic said:**
> ok, renamed the exe to remove the space and retried- got this error-
** (workingexample.exe:1686): WARNING **: The following assembly
referenced from /home/steve/Desktop/workingexample.exe could not be
loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    10.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed
in the MONO_PATH environment variable, or in the location of the
executing assembly (/home/steve/Desktop/).


** (workingexample.exe:1686): WARNING **: Could not load file or
assembly 'Microsoft.VisualBasic, Version=10.0.0.0, Culture=neutral,
PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded
[steve@steve-Satellite-PRO-L10:~/Desktop$]("wlmailhtml:{D760F779-3316-4300-A3CD-9F88E66CC1E7}mid://00003472/!x-usc:mailto:steve@steve-Satellite-PRO-L10:~/Desktop$") 

Thanks again chaps!
 
Steve

Right.

VB.NET 10.0.0.0 is the .NET 4.0 version.

As I said, we don't (yet) have packages which support this. The VB.NET support currently in Ubuntu goes as far as VB.NET 8.0.0.0 (2005) on .NET 3.5.

If you have the option to build against the older version in Visual Studio, do that (I don't know VS, so I don't know if that's possible)

Otherwise, you may need to either wait for Mono 2.8+ to arrive on Ubuntu, or try compiling it on Ubuntu rather than on Windows, using the Mono VB.NET compiler. This all assumes your app is even 2005-compatible, of course.

---

### Post by EccentricDyslexic on 2011-02-16
ok thanks for that.
 
i have loaded workingexample into mono develop and exported it(i expect this is the same as VS publish?) in vs2008 format.  but there is no .exe file. There is no Publish button anywhere...am i missing something?
 
steve

---

### Post by shunan on 2011-02-16
hi i would suggest to do a little bit of reading first

check the monodevelo features
[http://monodevelop.com/Documentation/Feature_List](http://monodevelop.com/Documentation/Feature_List)

export is used to export a project to a different folder using a different file formats, like MonoDevelop native file format or Visual Studio 2005.

what you need is Build (not export)

select Build -> Build All from the menu and then Run -> Debug to test it...

---

### Post by EccentricDyslexic on 2011-02-17
But wont that just do a debug build? is that the only way to run my app on Ubuntu then?  i cant publish it as a stand alone .exe?
 
anyway, i have done as you said but with my app in monodevelop on my windows7 laptop, just so i can get to grips with it before i try it on Ubuntu.  However i am getting an error, i think it is to do with a required .dll  With VS i had to put the .dll in windows32 folder, do i have to do something similar with monodevelop?
 
Belive me, i am trudging through the info scatered about on the net but much of it isnt very consise.
 
cheers
 
steve

---

### Post by directhex on 2011-02-17
> **EccentricDyslexic said:**
> However i am getting an error, i think it is to do with a required .dll  With VS i had to put the .dll in windows32 folder, do i have to do something similar with monodevelop?

You'll have to be specific about the error if you want a specific answer.

---

### Post by directhex on 2011-02-17
> **EccentricDyslexic said:**
> But wont that just do a debug build? is that the only way to run my app on Ubuntu then?  i cant publish it as a stand alone .exe?

A debug build is a normal build, with additional .mdb files for the Mono debugger, which you don't need to ship. Your solution is compiled into however many .dll and .exe files are detailed in the projects.

---

### Post by EccentricDyslexic on 2011-02-17
I:\projectraw\RIMs heater code sample\My Project\AssemblyInfo.vb(0,0): Warning BC40056: Namespace or type specified in the Imports 'System.Runtimere.InteropServices' doesn't contain any public member or cannot be found. Make sure the namespace or the type is defined and contains at least one public member. Make sure the imported element name doesn't use any aliases. (BC40056) (RIMs heater code sample)
 
Cheers
 
steve

---

### Post by directhex on 2011-02-17
Looks like a typo? Runtimere? There's a System.Runtime.InteropServices namespace...

---

### Post by EccentricDyslexic on 2011-02-18
yep it was a typo, not sure what happened there.
 
Now another error msg-
 
 error RG0000: Type System.Drawing.Point, System.Drawing, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a in the data at line 120, position 4 cannot be located. Line 122, position 5.
 
Cheers
 
steve

---

### Post by directhex on 2011-02-18
> **EccentricDyslexic said:**
> yep it was a typo, not sure what happened there.
 
Now another error msg-
 
 error RG0000: Type System.Drawing.Point, System.Drawing, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a in the data at line 120, position 4 cannot be located. Line 122, position 5.
 
Cheers
 
steve

What's at line 120? If it's a reference to a .resx file, make sure the case is correct on your .resources (Linux is case-sensitive) and make sure the .resx is being compiled in your project

---

### Post by EccentricDyslexic on 2011-02-18
line 120-
 
 <metadata name="Timer1.TrayLocation" type="System.Drawing.Point, System.Drawing, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
 
When i look in references system.drawing it is saying version 2, could that be an issue?
 
Im not sure what you mean about the case being correct in .recources, this is VS produced code, i didnt type it myself.  Also,, the .resx appears in the project from within monodevelop.
 
Cheers
 
steve

---

