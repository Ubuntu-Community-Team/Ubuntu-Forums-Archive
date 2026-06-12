---
title: "Firefox doesn't run applet, Opera does"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by dingorunner on 2008-04-06
Hello everyone and thanks for your time.
Well let's get to the point. I've run applets on firefox but I haven't been able to run this particular one: [http://www.unalmed.edu.co/~curmat/alineal/](http://www.unalmed.edu.co/~curmat/alineal/). There is supposed to be a Java written Menu on the left but instead there is a gray box. At the beginning firefox asked for Pluggins to be installed but once I installed them all it started behaving like this. One particular thing is that for some reason Opera Browser does run this menu-apple with no problem. 

Ubuntu/7.10 (gutsy) Firefox/2.0.0.13.  
I really don't understand most of this, but I hope It will give you more info:  
```

>firefox *(then from firefox I go http://www.unalmed.edu.co/~curmat/alineal/) *
GCJ PLUGIN: thread 0x805e520: NP_Initialize
GCJ PLUGIN: thread 0x805e520: NP_Initialize: using /usr/lib/classpath/gappletviewer.
GCJ PLUGIN: thread 0x805e520: NP_Initialize return
GCJ PLUGIN: thread 0x805e520: GCJ_New
GCJ PLUGIN: thread 0x805e520: plugin_data_new
GCJ PLUGIN: thread 0x805e520: plugin_data_new return
GCJ PLUGIN: thread 0x805e520: plugin_get_documentbase
GCJ PLUGIN: thread 0x805e520: plugin_get_documentbase return
GCJ PLUGIN: thread 0x805e520: plugin_start_appletviewer
GCJ PLUGIN: thread 0x805e520: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x805e520: GCJ_New: got confirmation that appletviewer is running.
GCJ PLUGIN: thread 0x805e520: plugin_create_applet_tag
GCJ PLUGIN: thread 0x805e520: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-6547-0
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote tag http://www.unalmed.edu.co/~curmat/alineal/Menu.htm <EMBED CODE="ButtonPopMenu.class" ARCHIVE="./Applet/popmenu.jar" HEIGHT="270" WIDTH="170" ><PARAM NAME="align" VALUE="left"><PARAM NAME="fuente" VALUE="Arial"><PARAM NAME="tamanoFuente" VALUE="14"><PARAM NAME="estiloFuente" VALUE="0"><PARAM NAME="colorFuente" VALUE="ffffff"><PARAM NAME="fuenteMenu" VALUE="Arial"><PARAM NAME="tamanoFuenteMenu" VALUE="13"><PARAM NAME="estiloFuenteMenu" VALUE="2"><PARAM NAME="popup" VALUE="derecha"><PARAM NAME="alinecionTexto" VALUE="centrado"><PARAM NAME="target" VALUE="mainFrame"><PARAM NAME="colorFondo" VALUE="fdf5e6"><PARAM NAME="colorBoton" VALUE="000080"><PARAM NAME="colorMouseOver" VALUE="0066ee"><PARAM NAME="espHorizontal" VALUE="0"><PARAM NAME="espVertical" VALUE="1"><PARAM NAME="tamdefecto" VALUE="no"><PARAM NAME="anchoBoton" VALUE="170"><PARAM NAME="altoBoton" VALUE="18"><PARAM NAME="orientacionBoton" VALUE="horizontal"><PARAM NAME="orientacionImagenV" VALUE="inferior"><PARAM NAME="orientacionImagenH" VALUE="izquierda"><PARAM NAME="archivo" VALUE="./Applet/menu.txt"></EMBED>
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: GCJ_New return
GCJ PLUGIN: thread 0x805e520: NP_GetValue
GCJ PLUGIN: thread 0x805e520: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e520: NP_GetValue return
GCJ PLUGIN: thread 0x805e520: GCJ_GetValue
GCJ PLUGIN: thread 0x805e520: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x805e520: GCJ_GetValue return
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-6547-0
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote handle 56635394
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow return
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-6547-0
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote width 170
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote instance-6547-0
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer
  PIPE: plugin wrote height 270
GCJ PLUGIN: thread 0x805e520: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x805e520: GCJ_SetWindow return
  PIPE: applet viewer wrote: running
  PIPE: applet viewer read: instance-6547-0
  PIPE: applet viewer read: tag http://www.unalmed.edu.co/~curmat/alineal/Menu.htm <EMBED CODE="ButtonPopMenu.class" ARCHIVE="./Applet/popmenu.jar" HEIGHT="270" WIDTH="170" ><PARAM NAME="align" VALUE="left"><PARAM NAME="fuente" VALUE="Arial"><PARAM NAME="tamanoFuente" VALUE="14"><PARAM NAME="estiloFuente" VALUE="0"><PARAM NAME="colorFuente" VALUE="ffffff"><PARAM NAME="fuenteMenu" VALUE="Arial"><PARAM NAME="tamanoFuenteMenu" VALUE="13"><PARAM NAME="estiloFuenteMenu" VALUE="2"><PARAM NAME="popup" VALUE="derecha"><PARAM NAME="alinecionTexto" VALUE="centrado"><PARAM NAME="target" VALUE="mainFrame"><PARAM NAME="colorFondo" VALUE="fdf5e6"><PARAM NAME="colorBoton" VALUE="000080"><PARAM NAME="colorMouseOver" VALUE="0066ee"><PARAM NAME="espHorizontal" VALUE="0"><PARAM NAME="espVertical" VALUE="1"><PARAM NAME="tamdefecto" VALUE="no"><PARAM NAME="anchoBoton" VALUE="170"><PARAM NAME="altoBoton" VALUE="18"><PARAM NAME="orientacionBoton" VALUE="horizontal"><PARAM NAME="orientacionImagenV" VALUE="inferior"><PARAM NAME="orientacionImagenH" VALUE="izquierda"><PARAM NAME="archivo" VALUE="./Applet/menu.txt"></EMBED>
  PIPE: applet viewer read: instance-6547-0
  PIPE: applet viewer read: handle 56635394

```

---

### Post by FuturePilot on 2008-04-06
It works fine here. By the errors you posted it looks like you're using the GCJ Java plugin which doesn't work very well as you can see.
You should try the Java 6 plugin
```
sudo apt-get remove --purge gcjwebplugin
```
then
```
sudo apt-get install sun-java6-plugin
```
and restart Firefox. Then try that page again.

---

### Post by dingorunner on 2008-04-06
Thanks a lot!
I removed GCJ Java plugin, and when I tried installing Java 6 Plugin it said that I alread have the most recent version, so I tried opening Firefox and the applet run correctly. I guess there was a incompatibility issues between both plugins. Anyways removing  GCJ Java plugin solved my problem. Thanks again.

---

