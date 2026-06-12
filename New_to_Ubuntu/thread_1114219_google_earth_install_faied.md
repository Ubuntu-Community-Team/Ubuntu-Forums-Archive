---
title: "google earth install faied"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by nutpants on 2009-04-02
i tried every way to install it i can think of or find.
make-googleearth-package. to the loki install..

all i get is this error

Warning: Unable to create prefs directory '/root/.googleearth'. File exists.
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin [0x806c3a3]
  ./googleearth-bin [0x806c916]
  [0xb8036400]
  /usr/lib/libX11.so.6(XInitExtension+0x41) [0xb650e771]
  /usr/lib/libXext.so.6(XextAddDisplay+0x52) [0xb65e7692]
  /usr/lib/libGL.so.1 [0xb603a58b]
  /usr/lib/libGL.so.1 [0xb603ae0f]
  /usr/lib/libGL.so.1 [0xb6037fcf]
  /opt/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext15setSwapIntervalEi+0x124) [0xb395d264]
  /opt/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x657) [0xb397d177]
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext11OpenContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0x101) [0xb3595021]
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x22d) [0xb35a010d]
  /opt/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x87) [0xb34878e7]
  ./librender.so(_ZN12RenderWidget6SetApiEPN5earth4evll3APIE+0x47) [0xb61c6277]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0xb2) [0xb61a7f62]
  ./libgoogleearth_lib.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x8e) [0xb6e0bf6e]
  ./libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0x7cf) [0xb777915f]
  ./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa8) [0xb7737130]
  ./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x122) [0xb773e916]
  ./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x9a) [0xb7e252f2]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x11f) [0xb777bfc3]
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7b) [0xb777bd0f]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb777be98]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb777c4bb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb777be82]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7b) [0xb777bd0f]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb777be98]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb777c4bb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb777be82]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb777c4bb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb777be82]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb777c4bb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb777be82]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb777c4bb]
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb777be82]
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb777bee6]
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb777c4bb]
  ./libQtGui.so.4(_ZN7QWidget10showNormalEv+0x4a) [0xb777180e]
  ./libgoogleearth_lib.so(_ZN10MainWindow18readScreensizeInfoEv+0xbfa) [0xb6ddd6ca]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application12SetupMainWinERK7QStringb+0x1f0) [0xb6e457d0]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x300) [0xb6e48140]
  ./googleearth-bin(main+0x2ba) [0x806da3a]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb6bd4685]
  ./googleearth-bin [0x806bb31]



i did update my ubuntu from 8.04 to 8.10  in the last two weeks..
google earth installed and ran fine before.

---

### Post by philinux on 2009-04-02
Click the medibuntu link below and follow the instructions. Then install via synaptic.

---

### Post by nutpants on 2009-04-05
tried that the fourth time around.
not worring about it much as i just noticed 9.04 will be out soon.\
but thanks..

nuts

---

### Post by GosthShadow on 2009-04-05
try to install in wine
):P

---

### Post by hyper_ch on 2009-04-05
wine is not required for GE.

---

### Post by Lunx on 2009-04-05
Having torn my hair out following all the advice and mis-advice I could findon getting GE to run, I can vouch that the suggestion from Phuilinux in post #2 up there ^ is the best way of getting it installed (medibuntu repository has v5 beta ). Make sure that step one is to follow the advice about enabling the Medibutu repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then once that is done you can find the package in Synaptic and install as usual.

I have found that every version of GE I've tried runs very buggy (if at all) when first started, but have worked out with advice cobbled together from several sources how I can get it to run. First of all, if it is playing up when you first try it, close GE and then switch from Compiz to Metacity. Restart GE and it should look better but it will probably now run as if half frozen, if this is the case you need to go to **View** in the GE menu and disable the **Atmosphere** setting and now hopefully all is good with the worlds again (both your own and Google's).

And remember to switch Compiz back on after, or you'll be wondering what happened to your effects :p.

Real PITA needing to use work arounds like this, hope Google get their act together and get this Linux version sorted (didn't I hear half of Google staff use Ubuntu? They must staff who don't use GE...)

Edit: I should have mentioned I tried this install method only about half an hour before writing this post and it worked well in Jaunty

---

