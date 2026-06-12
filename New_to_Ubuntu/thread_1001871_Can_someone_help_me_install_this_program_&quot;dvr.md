---
title: "Can someone help me install this program &quot;dvr&quot; from source?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Rob-e on 2008-12-04
i know there is an older version in the repos but it records to a green video (but it does show the image from the video card 'live') and i think that latest version will fix this

so heres the files im trying to install
[http://www.pierrox.net/dvr/releases/dvr-3.99.3.tar.bz2](http://www.pierrox.net/dvr/releases/dvr-3.99.3.tar.bz2)

and heres the makefile if you dont download the whole package
```
# edit these values to match your system
PREFIX=/usr/local
QT_INCLUDE=-I/usr/include/qt
QT_LIB=-L/usr/lib/qt -lqt-mt
GST_INCLUDE=$(shell pkg-config --cflags gstreamer-0.10)
GST_LIB=$(shell pkg-config --libs gstreamer-0.10)

DVR_VERSION=3.99.3

BUILD=../build

CFLAGS_ADD=-g
LDFLAGS_ADD=
CFLAGS=-DPREFIX="\"$(PREFIX)\"" -DDVR_VERSION="\"$(DVR_VERSION)\"" -W -Wall -I. -I$(BUILD) $(QT_INCLUDE) $(GST_INCLUDE) $(CFLAGS_ADD)
CXXFLAGS=$(CFLAGS)
LDFLAGS=$(QT_LIB) $(GST_LIB) $(LDFLAGS_ADD)

exe=dvr

ui=dvr_control.ui tab_audio_config.ui tab_codec_config.ui tab_general.ui tab_video_config.ui tab_monitoring.ui device_selection.ui property_editor.ui

ui_o=$(ui:%.ui=$(BUILD)/ui_%.o)
moc_o=$(ui:%.ui=$(BUILD)/moc_%.o)

objs=$(BUILD)/main.o \
     $(BUILD)/dvr.o \
     $(BUILD)/dvr_control.o \
     $(BUILD)/device_selection.o \
     $(BUILD)/tab_general.o \
     $(BUILD)/tab_audio_config.o \
     $(BUILD)/tab_codec_config.o \
     $(BUILD)/tab_video_config.o \
     $(BUILD)/tab_monitoring.o \
     $(BUILD)/property_editor.o \
     $(BUILD)/qlistbox_codec.o \
     $(BUILD)/qlistview_codec_property.o


all: init $(BUILD)/$(exe)

$(BUILD)/$(exe): $(ui:%.ui=$(BUILD)/ui_%.h) $(ui:%.ui=$(BUILD)/ui_%.cpp) $(objs:%.o=%.d) $(ui_o) $(moc_o) $(objs)
	g++ $(LDFLAGS) $(ui_o) $(moc_o) $(objs) -o $@
		  
init:
	mkdir -p $(BUILD)

$(BUILD)/%.o: %.cpp
	g++ -c -o $@ $*.cpp $(CXXFLAGS)

$(BUILD)/%.o: %.c
	gcc -c -o $@ $*.c $(CFLAGS)

$(BUILD)/%.o: $(BUILD)/%.cpp
	g++ -c -o $@ $(BUILD)/$*.cpp $(CXXFLAGS)

$(BUILD)/ui_%.h: %.ui
	uic $^ > $@

$(BUILD)/ui_%.cpp: $(BUILD)/ui_%.h
	uic -impl $< $*.ui > $@
	
$(BUILD)/moc_%.cpp: $(BUILD)/ui_%.h
	moc $^ -o $@

$(BUILD)/%.d: %.c
	cpp -MM $(CXXFLAGS) -MT $(BUILD)/$*.o $^ > $@ || (rm -f $@; exit 1)

$(BUILD)/%.d: %.cpp
	cpp -MM $(CXXFLAGS) -MT $(BUILD)/$*.o $^ > $@ || (rm -f $@; exit 1)

clean:
	rm -rf *~ $(BUILD)

dep: $(objs:%.o=%.d)

i18n_update: *.cpp $(ui)
	for l in de fr; do lupdate $^ -ts translations/dvr_$$l.ts; done

i18n_release:
	for l in de fr; do lrelease $^ translations/dvr_$$l.ts -qm $(BUILD)/dvr_$$l.qm; done

install: $(BUILD)/$(exe) i18n_release
	install -d -m 755 ${PREFIX}/bin
	install -d -m 755 ${PREFIX}/share/dvr-${DVR_VERSION}/translations
	install -d -m 755 ${PREFIX}/share/dvr-${DVR_VERSION}/doc
	install -s -m 755 $(BUILD)/$(exe) ${PREFIX}/bin
	install -m 644 $(BUILD)/*.qm ${PREFIX}/share/dvr-${DVR_VERSION}/translations
	install -m 644 ../doc/* ${PREFIX}/share/dvr-${DVR_VERSION}/doc

-include $(BUILD)/*.d

```

when i run the makefile it outputs:
```

rob@rob-laptop:~/Desktop/dvr-3.99.3/src$ sudo make
Package gstreamer-0.10 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gstreamer-0.10.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gstreamer-0.10' found
cpp -MM -DPREFIX="\"/usr/local\"" -DDVR_VERSION="\"3.99.3\"" -W -Wall -I. -I../build -I/usr/include/qt  -g -MT ../build/*.o device_selection.cpp dvr_control.cpp dvr.cpp main.cpp property_editor.cpp qlistbox_codec.cpp qlistview_codec_property.cpp tab_audio_config.cpp tab_codec_config.cpp tab_general.cpp tab_monitoring.cpp tab_video_config.cpp > ../build/*.d || (rm -f ../build/*.d; exit 1)
cpp: too many input files
mkdir -p ../build
uic tab_audio_config.ui > ../build/ui_tab_audio_config.h
/bin/sh: uic: not found
make: *** [../build/ui_tab_audio_config.h] Error 127
```

i have gstreamer .10 installed, so idk what to do, ive been trying to record video all morning ](*,)

---

### Post by oldos2er on 2008-12-04
In order to compile anything, you first need to install the package build-essential.

---

### Post by Rob-e on 2008-12-04
yep, i have that

and i got the gstreamer errors to go away by doing what was said here:
[http://ubuntuforums.org/showthread.php?t=680646](http://ubuntuforums.org/showthread.php?t=680646)

---

### Post by DieB on 2008-12-04
for meeting dependencies on compiling u will always need the packages ending with -dev.

if there might be more problems ;)

---

