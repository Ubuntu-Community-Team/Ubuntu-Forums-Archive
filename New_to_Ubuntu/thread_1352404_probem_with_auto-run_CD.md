---
title: "probem with auto-run CD"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by always_smile on 2009-12-11
I've got a learning CD,DVD that does auto-run when I play with windows,the folder in ubuntu showsshows some exe. files,a swf fileplus the icon of auto-run whick looks like a txt,non of the files work when I try to click them.
The exe files give this message: 
'Archive:  /media/cdrom0/Main.exe
[/media/cdrom0/Main.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Main.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Main.exe or
          /media/cdrom0/Main.exe.zip, and cannot find /media/cdrom0/Main.exe.ZIP, period'
While the SWF file gives the error:
GStreamer encountered a general supporting library error

How can I tackle this probelm,thank you for being helpful.

---

### Post by Daveth on 2009-12-11
it will not auto-play in the fashion you might expect as the windows .exe file will not natively run in ubuntu, and the content makers designed the whole thing to be displayed in that fashion.  You should still be able to get the .swf macromedia flash content though. Have you added the swfdec-gnome file to your system from the repository (system/admin/synaptic and type swfdec-gnome in the search) ? I would have thought double clicking the swf file should then launch your learning video.

You could try to run the whole dvd under the WINE program, which you can also download from the repository, though this seems a little over the top. If it is a simple loading program it should work fine though.

---

### Post by always_smile on 2009-12-12
> **Daveth said:**
> it will not auto-play in the fashion you might expect as the windows .exe file will not natively run in ubuntu, and the content makers designed the whole thing to be displayed in that fashion.  You should still be able to get the .swf macromedia flash content though. Have you added the swfdec-gnome file to your system from the repository (system/admin/synaptic and type swfdec-gnome in the search) ? I would have thought double clicking the swf file should then launch your learning video.

You could try to run the whole dvd under the WINE program, which you can also download from the repository, though this seems a little over the top. If it is a simple loading program it should work fine though.

Now I got WINE,but it gives me this error: component wmp.dll or one of its dependencies not correctly registered , a file is invalid or missing.
what can I do?
Another dvd works with WINE but the quality is rather poor,and the voice isn't good .

---

