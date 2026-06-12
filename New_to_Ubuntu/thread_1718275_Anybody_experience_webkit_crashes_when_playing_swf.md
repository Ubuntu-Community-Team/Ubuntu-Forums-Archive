---
title: "Anybody experience webkit crashes when playing swf files?"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by tomochan on 2011-03-31
Hi,
   I'm developing my own webkit client on Maverick with libwebkit-1.0 I installed from synaptic. My little webkit-based mini browser renders different HTML pages that are modified at run-time by my little browser itself. Sometimes I render a page with AVI movies, and sometime FLV files, and sometimes SWF files. And this run-time HTML manipulation is done by JavaScript functions that are called from within C++, and I did this by using Webkit's JavascriptCore APIs.
   However everything works fine until last night, my mini browser crashes while playing all SWF files.
   The JavaScript snippet I'm using to play SWF files are as below:
else if(type == "swf"){	
                $('#div0').html('<object id="FlashID" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" class="Main_Video_Frame">'+	
                                        '<param name="movie" value="'+src+'" />'+	
                                   '<param name="expressinstall" value="../../swf/expressInstall.swf" />'+
                                   '<param name="quality" value="high" />'+
                                        '<param name="wmode" value="opaque" />'+
                                   '<param name="swfversion" value="6.0.65.0" />'+
                                 '</object>');



   Any sharing or suggestion are appreciated in advance!!

---

### Post by tomochan on 2011-03-31
Just that I forgot the error message when my mini browser crashed on SWF files:
"The program 'GtkLauncher' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 17324 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"


Also that I tried gdb break on gdk_x_error() plus run --sync, but couldn't get any backtrace......

---

