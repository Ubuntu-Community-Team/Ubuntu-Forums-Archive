---
title: "need to copy the third party dependencies"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by sinbowden on 2011-08-10
I need help with finding and copying what this txt is talking about: You will additionally need to copy the third party dependencies (.dll and .config) from the
thirdparty and thirdparty/Tao directories into the game root:

    cp -v thirdparty/*.dll thirdparty/Tao/* .

---

### Post by michey_n on 2011-08-10
hey, i'm just a newbie to ubuntu but have you tried copying them using the nautilus not the command line...

---

### Post by sinbowden on 2011-08-10
Thank you.

---

### Post by idoitprone on 2011-08-10
> **sinbowden said:**
> I need help with finding and copying what this txt is talking about: You will additionally need to copy the third party dependencies (.dll and .config) from the
thirdparty and thirdparty/Tao directories into the game root:

    cp -v thirdparty/*.dll thirdparty/Tao/* .

I dont believe you need the * at the end

```
cp -v thirdparty/*.dll thirdparty/Tao/
```

Are you installing a window program? Linux does not use dlls so whatever your doing wont work without wine

---

### Post by sinbowden on 2011-08-10
I am trying to go through the installation txt for openra, because the game crashes at launch. wgen i try to run the openra CMD in the terminal i get this output: 

Using Gl renderer

Unhandled Exception: System.InvalidOperationException: GL Error: 1282
  at OpenRA.Renderer.Glsl.GraphicsDevice.CheckGlError () [0x00000] in <filename unknown>:0                            
  at OpenRA.Renderer.Glsl.Shader..ctor (OpenRA.Renderer.Glsl.GraphicsDevice dev, System.String type) [0x00000] in <filename unknown>:0                                           
  at OpenRA.Renderer.Glsl.GraphicsDevice.CreateShader (System.String name) [0x00000] in <filename unknown>:0          
  at OpenRA.Graphics.Renderer..ctor () [0x00000] in <filename unknown>:0                                              
  at OpenRA.Game.Initialize (OpenRA.Arguments args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 


I thought it was because I needed to do something with these files? now i know they are windows only files!

---

### Post by Mark Phelps on 2011-08-10
First of all, don't go hacking around copying Windows .DLL files just because you can.  Wine uses its own CUSTOM DLL files and if you replace any of those, it will not work anymore.

Second, my guess is that you're encountering a graphics driver problem -- which is NOT solved by copying Windows files onto your Linux install.

IF you know the make and model videocard, then post that here.  If you don't, open a terminal, enter "lspci", look for the line containing "VGA" -- and post that here.

---

