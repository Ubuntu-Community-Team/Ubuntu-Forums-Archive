---
title: "FreeMotion 2008 crashing on start"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by grtwhiterhyno on 2009-05-22
i have wine 1.0 on red heron
i got namo's webeditor to work by downloading and overriding a couple of .dll's.
but im struggling with its counterpart FreeMotion, a flash editor. here is what i get back in terminal:

######:~/.wine/drive_c/Program Files/Namo/FreeMotion 2008$ wine FreeMotion.exe
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id 191, flags 0x8!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x1
err:ole:ITypeInfo_fnInvoke did not find member id 191, flags 0x8!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:imm:ImmReleaseContext (0x1044c, 0x13a730): stub
fixme:win:AnimateWindow partial stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Namo\\FreeMotion 2008\\nmlicui.dll") not found

i have added and overridden import.dll, mixer.dll, and mfc42u.dll. none were listed in the library in the winecfg so typed them in per instruction after putting them in my system32 folder. what do i need to do now.

---

### Post by grtwhiterhyno on 2009-05-22
my appologies guys
as i typed that i realized i had mfc42"u".dll and not the mfc42.dll. after putting it in, my problem was solved. thank you for your time.

---

