---
title: "install The Legend of Zelda: Storms of Evil 0.2 for Linux?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by steigerjb on 2009-12-14
How do I install The Legend of Zelda: Storms of Evil 0.2 for Linux?

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/The-Legend-of-Zelda-Storms-of-Evil-31404.shtml]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/The-Legend-of-Zelda-Storms-of-Evil-31404.shtml")

---

### Post by Bachstelze on 2009-12-14
In the source archive, you have a [font=monospace]compile.sh[/font] script, run it. You need to install [font=monospace]liballegro4.2-dev[/font] beforehand.

---

### Post by synapsys on 2009-12-14
for future reference, always read the readme.txt file.

> Linux/Unix Notes | To compile, someply run compile.sh and run        |
+------------------+ unixsoe.  There should be a precompile version,    |
| but sometimes it might not work.  You may need the new Allegro     |
| Library from [http://alleg.sf.net](http://alleg.sf.net).  If you encounter any errors,    |
| please report them to the url listed above.    

---

### Post by steigerjb on 2009-12-14
> **Bachstelze said:**
> In the source archive, you have a [font=monospace]compile.sh[/font] script, run it. You need to install [font=monospace]liballegro4.2-dev[/font] beforehand.

i ran the compile.sh in terminal. it ran for a split second and closed :(

---

### Post by steigerjb on 2009-12-14
> **Bachstelze said:**
> In the source archive, you have a [font=monospace]compile.sh[/font] script, run it. You need to install [font=monospace]liballegro4.2-dev[/font] beforehand.

k, this time i tried drag and dropping in terminal

```
joe@joe-laptop:~$ '/home/joe/Games/soe-linux-0.2/compile.sh' 
Compiling SoE
g++: main.cpp: No such file or directory
Finished.
joe@joe-laptop:~$ 
```

---

### Post by natravis on 2009-12-14
g++ is a compiler. You probably need to install the build-essential package.
Open a terminal and use
```
sudo apt-get install build-essential
```
while online. Try to run the compile script after installing that package. It is required to compile anything.

Hope it's helpful!

---

### Post by steigerjb on 2009-12-15
> **natravis said:**
> g++ is a compiler. You probably need to install the build-essential package.
Open a terminal and use
```
sudo apt-get install build-essential
```
while online. Try to run the compile script after installing that package. It is required to compile anything.

Hope it's helpful!

```
joe@joe-laptop:~$ sudo apt-get install build-essential
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  gnuplot gnustep-base-common dvdrip-doc python-pexpect xulrunner-1.9.2
  xulrunner-1.9.3 libavahi-compat-libdnssd1 libevent-execflow-perl
  gnustep-base-runtime groff libnet-ssleay-perl twolame librsvg2-2.18-cil
  gnustep-gui-common libintl-perl libgdata1.4-cil libapm1 transcode-utils
  gnustep-back0.16 transcode-doc transfig libgnustep-gui0.16 mencoder
  subtitleripper gnustep-back0.16-art libxine1-ffmpeg gnuplot-x11
  libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl libgnustep-base1.19
  gnustep-common gnuplot-nox lsdvd vamps libnspr4-dev transcode gnustep-gpbs
  fping netpbm libwnck2.20-cil anyevent-perl sox psutils gocr libevent-perl
  libnetpbm10 mjpegtools gnustep-back-common xine-ui libacpi0 libobjc2
  libio-socket-ssl-perl mkvtoolnix gnustep-gui-runtime libjpeg-progs
  libgnomedesktop2.20-cil libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joe-laptop:~$ 
```

---

### Post by KIAaze on 2009-12-15
> **steigerjb said:**
> k, this time i tried drag and dropping in terminal

```
joe@joe-laptop:~$ '/home/joe/Games/soe-linux-0.2/compile.sh' 
Compiling SoE
g++: main.cpp: No such file or directory
Finished.
joe@joe-laptop:~$ 
```

It seems you haven't changed into the source directory.
Try:
```
cd /home/joe/Games/soe-linux-0.2/
./compile.sh

```

P.S.: Official site and sourceforge page:
[http://sourceforge.net/projects/soe/](http://sourceforge.net/projects/soe/)
[http://soe.sourceforge.net/](http://soe.sourceforge.net/)

What I found strange was this message on the SF page:
> Pulling Source, and GPL

As of now, SoE will no longer continue to be a GPL program, which means no more Linux releases. This decision will also mean that SoE will no longer be hosted on sourceforge, although the exact location of the new address is not known. We WILL continue to make releases of SoE for the Win32 platform, but new versions will be few because the current development platform is Linux.

posted by codyhs 2072 days ago

:confused:

---

### Post by Maheriano on 2009-12-15
So they're using the game names without permission?

---

### Post by steigerjb on 2009-12-15
> **KIAaze said:**
> It seems you haven't changed into the source directory.
Try:
```
cd /home/joe/Games/soe-linux-0.2/
./compile.sh

```


```
joe@joe-laptop:~$ cd /home/joe/Games/soe-linux-0.2/
joe@joe-laptop:~/Games/soe-linux-0.2$ ./compile.sh
Compiling SoE
In file included from main.cpp:42:
modules.h:7:20: error: aldumb.h: No such file or directory
In file included from main.cpp:42:
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
modules.h:57: warning: deprecated conversion from string constant to ‘char*’
main.cpp: In function ‘int main(int, char**)’:
main.cpp:78: error: ‘dumb_register_stdfiles’ was not declared in this scope
main.cpp:79: error: ‘dumb_register_packfiles’ was not declared in this scope
In file included from main.cpp:145:
intro.h:9: error: ‘AL_DUH_PLAYER’ was not declared in this scope
intro.h:9: error: ‘intromusic’ was not declared in this scope
intro.h:10: error: ‘DUMBFILE’ was not declared in this scope
intro.h:10: error: ‘introfile’ was not declared in this scope
intro.h:11: error: ‘DUH’ was not declared in this scope
intro.h:11: error: ‘intromusic_duh’ was not declared in this scope
intro.h:12: error: ‘dumbfile_open_memory’ was not declared in this scope
intro.h:13: error: ‘dumb_read_it’ was not declared in this scope
In file included from main.cpp:145:
intro.h:14: error: ‘al_start_duh’ was not declared in this scope
intro.h:45: error: ‘dumb_exit’ was not declared in this scope
intro.h:70: error: ‘al_poll_duh’ was not declared in this scope
intro.h:75: error: ‘al_stop_duh’ was not declared in this scope
main.cpp:222: error: ‘overworld_player’ was not declared in this scope
main.cpp:223: error: ‘overworld_file’ was not declared in this scope
main.cpp:224: error: ‘overworld_duh’ was not declared in this scope
main.cpp:276: warning: ‘void yield_timeslice()’ is deprecated (declared at /usr/include/allegro/alcompat.h:211)
main.cpp:276: warning: ‘void yield_timeslice()’ is deprecated (declared at /usr/include/allegro/alcompat.h:211)
main.cpp:314: error: ‘al_poll_duh’ was not declared in this scope
main.cpp:341: warning: ‘void yield_timeslice()’ is deprecated (declared at /usr/include/allegro/alcompat.h:211)
main.cpp:341: warning: ‘void yield_timeslice()’ is deprecated (declared at /usr/include/allegro/alcompat.h:211)
main.cpp:351: error: ‘dumb_exit’ was not declared in this scope
Finished.
joe@joe-laptop:~/Games/soe-linux-0.2$ 

```

---

### Post by natravis on 2009-12-15
Well, the version of the program is over 2 years old. From your output, it seems that there are many lines in the code that are deprecated (meaning have been replaced or gone out of use) and perhaps the way the compiler is used has changed dramatically (the lines about void function() being deprecated). I don't forsee this working on a recent system.

---

### Post by KIAaze on 2009-12-15
This worked for me to compile it:
```
sudo apt-get install libaldmb1-dev
g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`

```

However, I get an alsa error when trying to run it:
```
$ ./soeunix
INIT: IDENT: LOZSOE
INIT: Internel program name: The Legend of Zelda: Storm of Evil
INIT: Starting intenal proceedures.
ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such file or directory

```
+ an xmessage:
```
Error initialising sound system
ALSA: snd_pcm_hw_params_set_format(pcm_handle, hwparams, format) : Invalid argument

```

I think it's possible to get it to run, but it might take some work. Modifying the source code may be necessary.

edit:
I managed to run it by simply deactivating the sound. It doesn't seem to be playable unfortunately.
All you can do is move Link around on a green background.

If you want to try it, here's the modified main.cpp I used:
```
/* The Legend Of Zelda: Storms of Evil
    Credits:
        Produced by:
                Adam Cook (a.k.a. Blue Falkon/CC)
        
        Game Programming by:  
                Vectec Software Inc. (http://vectec.net)

        Game Concept by:
                Adam Cook (a.k.a. Blue Falkon/CC)

        Graphics by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Gad Deutcsh (a.k.a. StellarWind Elsydeon)
                Cody Harris
        
        Level Design by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Ruben Sibon (MadMoblin)

        Music compositions by:
                Johnathan Palmer (Morphix)
                Adam Cook (a.k.a. Blue Falkon/CC)

        Special thanks to:

        Zelda is a registered trademark of Nintendo International
    
    Info:
        Storms of evil is a Zelda game built from C++ and allegro, using sheets
        from Open Zelda as well as some custom ones.
        
*/
#include <iostream>
#include <stdlib.h>
#include <string>
#include <fstream>
#include <vector>
#include <cstdlib>

//Ok, lets dynamically load any libraries we need.
#include "modules.h"
#define P_NAME "The Legend of Zelda: Storm of Evil"
#include "outside_tile.h"

BITMAP *linkbuffer;


int convert (BITMAP *todump, char* filename);

int main(int argc, char *argv[])
{
	//Titlescreen Music
	MIDI *the_music;

	//Buffer
	char buf[256];

	//Outside sheet Init
	BITMAP *tile_buffer;
	BITMAP *buffer;
	BITMAP *screen_buffer;
    
	//Default File:
	string szfile("soelevel.txt");
   	string szline;
	cout << "INIT: IDENT: LOZSOE" << endl;
	cout << "INIT: Internel program name: " << P_NAME << endl;
	cout << "INIT: Starting intenal proceedures." << endl;
	if (allegro_init()){
		cout << "INIT: Unable to load Allgero!" << endl;
		return 1;
	}


	//DUMB INIT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
	//atexit(&dumb_exit);
	dumb_register_stdfiles();
	dumb_register_packfiles();



	set_window_title("SoE: INIT");
	if(install_timer()){
		cout << "INIT: Error installing timer." << endl;
		return 1;
	}
	install_keyboard(); 


     
     //timer related stuff
     LOCK_VARIABLE(gtimer);
     LOCK_FUNCTION(gamtimer);
     install_int_ex(gametimer, BPS_TO_TIMER(80));

//      if (install_sound(DIGI_AUTODETECT, MIDI_AUTODETECT, argv[0]) != 0) {
//           allegro_message("Error initialising sound system\n%s\n", allegro_error);
//           return 1;
//      }


    cout << "INIT: Ready to launch core." << endl;
    if (desktop_color_depth() < 8){
        cout << "This game requires at least 15 bit colour depth." << endl;
        return 1;
    }else{
        cout << "INIT: Color Depth OK (" << desktop_color_depth() << ")" << endl;
    }
    set_color_depth(24);
    
    if (set_gfx_mode(GFX_AUTODETECT_WINDOWED, 640, 480, 0, 0)){
        cout << "INIT: Error setting res. Attempted windowed." << endl;
        system ("pause");
        return 1; 
    }
    clear_to_color(screen, makecol(127, 127, 255));
    //text_mode(-1);
    textout_centre_ex(screen, font, "Please Wait", SCREEN_W/2, SCREEN_H/2 - 20, makecol(255,255,255), -1);
    textout_centre_ex(screen, font, "SoE is Loading...This may take a while", SCREEN_W/2, SCREEN_H/2 + 20, makecol(255,255,255), -1);
    cout << "INIT: Loading Datafile: ";
     if((soe_datafile=load_datafile("soe.dat"))==NULL) {
          cout << "Error loading soe.dat" << endl;
          system ("PAUSE");
          exit(1);
     }
     cout << " OK" << endl;
     the_music = (MIDI *)soe_datafile[soe_title].dat;
     if (!the_music) {
          allegro_message("Error reading MIDI file '%s'\n", argv[1]);
          return 1;
      }
     cout << "INIT: MIDI Set up and ready!" << endl;
	if (midi_driver){
		cout << "INIT: Music Driver: " << midi_driver->name << endl;
	}
    tilesheet2 osheet1((BITMAP *)soe_datafile[soe_os1].dat);
    tilesheet2 playsheet1((BITMAP *)soe_datafile[soe_playsheet1].dat);
    tilesheet2 soelogo((BITMAP *)soe_datafile[soe_logo].dat);
    tilesheet2 bglayer((BITMAP *)soe_datafile[soe_bglayer].dat);
    int y;
    int x;
    set_window_title("SoE: Welcome to SoE");
	cout << "Loading Intro..." << endl;
#include "intro.h"


    osheet1.settileindexoffset (8,0);
    tile_buffer = osheet1.retbitmaptileindex(11,1);
    
    if (!tile_buffer){
        cout << "ERROR!" << tile_buffer->h << endl;
    }
    //Create screen buffer to remove ugly generation
    buffer = create_bitmap(800, 600);
    screen_buffer = create_bitmap (640, 480);
    linkbuffer = create_bitmap (16,24);

    //for (x = 0; x < 800; x += 16){
    //    for (y = 0; y < 600; y += 16){
    //            blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
    //    }
    //}
    //for (x = 2; x < 38; x++){
    //    draw_tile_grid(osheet1.retbitmaptileindex(8,0), buffer, x, 8);
    //}
        //draw_tile_grid(osheet1.retbitmaptileindex(11,0), buffer, 45, 10);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,1), buffer, 45, 11);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,2), buffer, 45, 12);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,3), buffer, 45, 13);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,4), buffer, 45, 14);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,5), buffer, 45, 15);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,6), buffer, 45, 16);
    int runninggame = 0;

    lastbeat = gtimer;
    int xplayer = 32;
    int yplayer = 32;
    int x_scroll = 0;
    int y_scroll = 0;
    int rereblit = 1;
    rect(buffer, 0, 0, 799, 599, 0);

    //SPRITE DECS
        //BODY
    RLE_SPRITE *link_body_stand_south;
    RLE_SPRITE *link_body_stand_north;
    RLE_SPRITE *link_body_stand_east;
    RLE_SPRITE *link_body_stand_west;

        //HEAD
    RLE_SPRITE *link_head_look_south;
    RLE_SPRITE *link_head_look_north;
    RLE_SPRITE *link_head_look_east;
    RLE_SPRITE *link_head_look_west;

    //SPIRTE MAKES
        //BODY
    link_body_stand_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,1));
    link_body_stand_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,1));
    link_body_stand_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,1));
    link_body_stand_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,1));

        //HEAD    
    link_head_look_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,0));
    link_head_look_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,0));
    link_head_look_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,0));
    link_head_look_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,0));

    clear_to_color(linkbuffer, makecol(255, 0, 255));    
    draw_rle_sprite(linkbuffer, link_body_stand_south, 0, 8);
    draw_rle_sprite(linkbuffer, link_head_look_south, 0, 0);
    int whichscreen = 0;
    int movelinkby = 2;
    int pos = 2;
    int stand = 1;
    int envync = 0;
    set_window_title("SoE: Testbed # 1");


	//Shiney new IT support!
	AL_DUH_PLAYER *overworld_player;
	DUMBFILE *overworld_file;
	DUH *overworld_duh;
	overworld_file = dumbfile_open_memory((char*)soe_datafile[soe_overworld].dat, soe_datafile[soe_title_track].size);
	overworld_duh = dumb_read_it(overworld_file);
	overworld_player = al_start_duh(overworld_duh, 2, 0, 1.0f, get_config_int("sound", "buffer_size", 4096), get_config_int("sound", "sound_freq", 44100));

    //OLD WAV SUPPORT
    //play_sample((SAMPLE *)soe_datafile[soe_overworld].dat, 255, 127, 1000, 1);

    //OLD MIDI SUPPORT
    //play_midi((MIDI *)soe_datafile[soe_lightover].dat, TRUE);

        int linenum = 0;
        int binnum = 0;
        char xx;
        int nchar = 0;
        int xtilecoord = 0;
        int ytilecoord = 0;
    	fstream startf(szfile.c_str(), ios_base::in);
    	if (!startf){
		    	cout << "INIT [FATAL]: File not found" << endl;
		    	return 1;
    	}
	cout << "INIT: Opened " << szfile.c_str() << " for reading." << endl;
    	while (!startf.eof()){
			startf.get(xx);
			if (xx == '\n'){
		    		linenum++;
		    		if (linenum == 1){
                        		binnum = atoi(szline.c_str());
					xtilecoord = (binnum & 15872) / 512;
					ytilecoord = (binnum & 496) / 16;
					osheet1.settileindexoffset (8,0);
					tile_buffer = osheet1.retbitmaptileindex(xtilecoord,ytilecoord);
					for (x = 0; x < 800; x += 16){
						for (y = 0; y < 600; y += 16){
							blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
						}
					}
				}else{
					cout << "Ignoring Line: " << linenum << endl;
				}
				
				nchar = 0;
				szline.erase();
			}else{
				szline += xx;
				nchar++;
			}
	}


    while (runninggame == 0){
    yield_timeslice();
        if (keypressed()){
                k = readkey();
                if (key[KEY_ESC]){
                                cout << "ENDING GAME" << endl;
                                runninggame = 1;
                }
                if (key[KEY_UP]){
                                yplayer -= movelinkby;
                                rereblit = 1;
                                pos = 0;
                }else if (key[KEY_DOWN]){
                                yplayer += movelinkby;
                                rereblit = 1;
                                pos = 2;
                }
                if (key[KEY_RIGHT]){
                                xplayer += movelinkby;
                                rereblit = 1;
                                pos = 1;
                }else if (key[KEY_LEFT]){
                                xplayer -= movelinkby;
                                rereblit = 1;
                                pos = 3;
                }
                if (key[KEY_V]){
                                if (envync == 1){
                                                                envync = 0;
                                                                textout_ex(screen, font, "VSync Diabled", 10, 10, makecol(0,0,0),-1);
                                }else{
                                                                envync = 1;
                                                                textout_ex(screen, font, "VSync Enabled", 10, 10, makecol(0,0,0),-1);
                                }
                }
        }

    if (lastbeat != gtimer){
	//The new system forces us to manually poll it.
	al_poll_duh(overworld_player);
    if (rereblit == 1){
        if (envync == 1){
                vsync();
        }
        blit (buffer, screen_buffer, x_scroll, y_scroll, 0, 0, 640, 480);
        if (stand){
                if (pos == 0){
                                draw_rle_sprite(screen_buffer, link_body_stand_north, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_north, xplayer, yplayer);
                }else if (pos == 2){
                                draw_rle_sprite(screen_buffer, link_body_stand_south, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_south, xplayer, yplayer);
                }else if (pos == 1){
                                draw_rle_sprite(screen_buffer, link_body_stand_east, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_east, xplayer, yplayer);
                }else if (pos == 3){
                                draw_rle_sprite(screen_buffer, link_body_stand_west, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_west, xplayer, yplayer);
                }
        }                                
        blit (screen_buffer, screen, 0, 0, 0, 0, 640, 480);

        rereblit = 0;
        clear_keybuf();
    }
    lastbeat = gtimer;
    yield_timeslice();
    }
    }
        
    set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
  cout << "INIT: Closing down internal proceedures." << endl;

	al_stop_duh(overworld_player);
  remove_sound();
  allegro_message ("Thank you for using SoE.");
	dumb_exit();
  allegro_exit();
  cout << "INIT: Goodbye!" << endl;
  return 0;
}

END_OF_MAIN();

```

Note:
I simply commented out the following lines:
```
      if (install_sound(DIGI_AUTODETECT, MIDI_AUTODETECT, argv[0]) != 0) {
           allegro_message("Error initialising sound system\n%s\n", allegro_error);
           return 1;
      }
```

---

### Post by KIAaze on 2009-12-16
Forgot to mention something that might be useful to you in the future:

When compiling from source and getting error messages about missing files (which are not in the downloaded source code), try using [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find the corresponding package. ;)

ex:
```
modules.h:7:20: error: aldumb.h: No such file or directory
```
lead me to this (search package contents):
[http://packages.ubuntu.com/search?searchon=contents&keywords=aldumb.h&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=aldumb.h&mode=exactfilename&suite=karmic&arch=any)

You can also use tools like apt-file:
[http://www.debuntu.org/how-to-find-missing-packages-with-apt-file](http://www.debuntu.org/how-to-find-missing-packages-with-apt-file)

---

### Post by steigerjb on 2009-12-16
> **KIAaze said:**
> This worked for me to compile it:
```
sudo apt-get install libaldmb1-dev
g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`

```

However, I get an alsa error when trying to run it:
```
$ ./soeunix
INIT: IDENT: LOZSOE
INIT: Internel program name: The Legend of Zelda: Storm of Evil
INIT: Starting intenal proceedures.
ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such file or directory

```
+ an xmessage:
```
Error initialising sound system
ALSA: snd_pcm_hw_params_set_format(pcm_handle, hwparams, format) : Invalid argument

```

I think it's possible to get it to run, but it might take some work. Modifying the source code may be necessary.

edit:
I managed to run it by simply deactivating the sound. It doesn't seem to be playable unfortunately.
All you can do is move Link around on a green background.

If you want to try it, here's the modified main.cpp I used:
```
/* The Legend Of Zelda: Storms of Evil
    Credits:
        Produced by:
                Adam Cook (a.k.a. Blue Falkon/CC)
        
        Game Programming by:  
                Vectec Software Inc. (http://vectec.net)

        Game Concept by:
                Adam Cook (a.k.a. Blue Falkon/CC)

        Graphics by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Gad Deutcsh (a.k.a. StellarWind Elsydeon)
                Cody Harris
        
        Level Design by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Ruben Sibon (MadMoblin)

        Music compositions by:
                Johnathan Palmer (Morphix)
                Adam Cook (a.k.a. Blue Falkon/CC)

        Special thanks to:

        Zelda is a registered trademark of Nintendo International
    
    Info:
        Storms of evil is a Zelda game built from C++ and allegro, using sheets
        from Open Zelda as well as some custom ones.
        
*/
#include <iostream>
#include <stdlib.h>
#include <string>
#include <fstream>
#include <vector>
#include <cstdlib>

//Ok, lets dynamically load any libraries we need.
#include "modules.h"
#define P_NAME "The Legend of Zelda: Storm of Evil"
#include "outside_tile.h"

BITMAP *linkbuffer;


int convert (BITMAP *todump, char* filename);

int main(int argc, char *argv[])
{
	//Titlescreen Music
	MIDI *the_music;

	//Buffer
	char buf[256];

	//Outside sheet Init
	BITMAP *tile_buffer;
	BITMAP *buffer;
	BITMAP *screen_buffer;
    
	//Default File:
	string szfile("soelevel.txt");
   	string szline;
	cout << "INIT: IDENT: LOZSOE" << endl;
	cout << "INIT: Internel program name: " << P_NAME << endl;
	cout << "INIT: Starting intenal proceedures." << endl;
	if (allegro_init()){
		cout << "INIT: Unable to load Allgero!" << endl;
		return 1;
	}


	//DUMB INIT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
	//atexit(&dumb_exit);
	dumb_register_stdfiles();
	dumb_register_packfiles();



	set_window_title("SoE: INIT");
	if(install_timer()){
		cout << "INIT: Error installing timer." << endl;
		return 1;
	}
	install_keyboard(); 


     
     //timer related stuff
     LOCK_VARIABLE(gtimer);
     LOCK_FUNCTION(gamtimer);
     install_int_ex(gametimer, BPS_TO_TIMER(80));

//      if (install_sound(DIGI_AUTODETECT, MIDI_AUTODETECT, argv[0]) != 0) {
//           allegro_message("Error initialising sound system\n%s\n", allegro_error);
//           return 1;
//      }


    cout << "INIT: Ready to launch core." << endl;
    if (desktop_color_depth() < 8){
        cout << "This game requires at least 15 bit colour depth." << endl;
        return 1;
    }else{
        cout << "INIT: Color Depth OK (" << desktop_color_depth() << ")" << endl;
    }
    set_color_depth(24);
    
    if (set_gfx_mode(GFX_AUTODETECT_WINDOWED, 640, 480, 0, 0)){
        cout << "INIT: Error setting res. Attempted windowed." << endl;
        system ("pause");
        return 1; 
    }
    clear_to_color(screen, makecol(127, 127, 255));
    //text_mode(-1);
    textout_centre_ex(screen, font, "Please Wait", SCREEN_W/2, SCREEN_H/2 - 20, makecol(255,255,255), -1);
    textout_centre_ex(screen, font, "SoE is Loading...This may take a while", SCREEN_W/2, SCREEN_H/2 + 20, makecol(255,255,255), -1);
    cout << "INIT: Loading Datafile: ";
     if((soe_datafile=load_datafile("soe.dat"))==NULL) {
          cout << "Error loading soe.dat" << endl;
          system ("PAUSE");
          exit(1);
     }
     cout << " OK" << endl;
     the_music = (MIDI *)soe_datafile[soe_title].dat;
     if (!the_music) {
          allegro_message("Error reading MIDI file '%s'\n", argv[1]);
          return 1;
      }
     cout << "INIT: MIDI Set up and ready!" << endl;
	if (midi_driver){
		cout << "INIT: Music Driver: " << midi_driver->name << endl;
	}
    tilesheet2 osheet1((BITMAP *)soe_datafile[soe_os1].dat);
    tilesheet2 playsheet1((BITMAP *)soe_datafile[soe_playsheet1].dat);
    tilesheet2 soelogo((BITMAP *)soe_datafile[soe_logo].dat);
    tilesheet2 bglayer((BITMAP *)soe_datafile[soe_bglayer].dat);
    int y;
    int x;
    set_window_title("SoE: Welcome to SoE");
	cout << "Loading Intro..." << endl;
#include "intro.h"


    osheet1.settileindexoffset (8,0);
    tile_buffer = osheet1.retbitmaptileindex(11,1);
    
    if (!tile_buffer){
        cout << "ERROR!" << tile_buffer->h << endl;
    }
    //Create screen buffer to remove ugly generation
    buffer = create_bitmap(800, 600);
    screen_buffer = create_bitmap (640, 480);
    linkbuffer = create_bitmap (16,24);

    //for (x = 0; x < 800; x += 16){
    //    for (y = 0; y < 600; y += 16){
    //            blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
    //    }
    //}
    //for (x = 2; x < 38; x++){
    //    draw_tile_grid(osheet1.retbitmaptileindex(8,0), buffer, x, 8);
    //}
        //draw_tile_grid(osheet1.retbitmaptileindex(11,0), buffer, 45, 10);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,1), buffer, 45, 11);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,2), buffer, 45, 12);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,3), buffer, 45, 13);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,4), buffer, 45, 14);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,5), buffer, 45, 15);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,6), buffer, 45, 16);
    int runninggame = 0;

    lastbeat = gtimer;
    int xplayer = 32;
    int yplayer = 32;
    int x_scroll = 0;
    int y_scroll = 0;
    int rereblit = 1;
    rect(buffer, 0, 0, 799, 599, 0);

    //SPRITE DECS
        //BODY
    RLE_SPRITE *link_body_stand_south;
    RLE_SPRITE *link_body_stand_north;
    RLE_SPRITE *link_body_stand_east;
    RLE_SPRITE *link_body_stand_west;

        //HEAD
    RLE_SPRITE *link_head_look_south;
    RLE_SPRITE *link_head_look_north;
    RLE_SPRITE *link_head_look_east;
    RLE_SPRITE *link_head_look_west;

    //SPIRTE MAKES
        //BODY
    link_body_stand_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,1));
    link_body_stand_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,1));
    link_body_stand_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,1));
    link_body_stand_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,1));

        //HEAD    
    link_head_look_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,0));
    link_head_look_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,0));
    link_head_look_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,0));
    link_head_look_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,0));

    clear_to_color(linkbuffer, makecol(255, 0, 255));    
    draw_rle_sprite(linkbuffer, link_body_stand_south, 0, 8);
    draw_rle_sprite(linkbuffer, link_head_look_south, 0, 0);
    int whichscreen = 0;
    int movelinkby = 2;
    int pos = 2;
    int stand = 1;
    int envync = 0;
    set_window_title("SoE: Testbed # 1");


	//Shiney new IT support!
	AL_DUH_PLAYER *overworld_player;
	DUMBFILE *overworld_file;
	DUH *overworld_duh;
	overworld_file = dumbfile_open_memory((char*)soe_datafile[soe_overworld].dat, soe_datafile[soe_title_track].size);
	overworld_duh = dumb_read_it(overworld_file);
	overworld_player = al_start_duh(overworld_duh, 2, 0, 1.0f, get_config_int("sound", "buffer_size", 4096), get_config_int("sound", "sound_freq", 44100));

    //OLD WAV SUPPORT
    //play_sample((SAMPLE *)soe_datafile[soe_overworld].dat, 255, 127, 1000, 1);

    //OLD MIDI SUPPORT
    //play_midi((MIDI *)soe_datafile[soe_lightover].dat, TRUE);

        int linenum = 0;
        int binnum = 0;
        char xx;
        int nchar = 0;
        int xtilecoord = 0;
        int ytilecoord = 0;
    	fstream startf(szfile.c_str(), ios_base::in);
    	if (!startf){
		    	cout << "INIT [FATAL]: File not found" << endl;
		    	return 1;
    	}
	cout << "INIT: Opened " << szfile.c_str() << " for reading." << endl;
    	while (!startf.eof()){
			startf.get(xx);
			if (xx == '\n'){
		    		linenum++;
		    		if (linenum == 1){
                        		binnum = atoi(szline.c_str());
					xtilecoord = (binnum & 15872) / 512;
					ytilecoord = (binnum & 496) / 16;
					osheet1.settileindexoffset (8,0);
					tile_buffer = osheet1.retbitmaptileindex(xtilecoord,ytilecoord);
					for (x = 0; x < 800; x += 16){
						for (y = 0; y < 600; y += 16){
							blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
						}
					}
				}else{
					cout << "Ignoring Line: " << linenum << endl;
				}
				
				nchar = 0;
				szline.erase();
			}else{
				szline += xx;
				nchar++;
			}
	}


    while (runninggame == 0){
    yield_timeslice();
        if (keypressed()){
                k = readkey();
                if (key[KEY_ESC]){
                                cout << "ENDING GAME" << endl;
                                runninggame = 1;
                }
                if (key[KEY_UP]){
                                yplayer -= movelinkby;
                                rereblit = 1;
                                pos = 0;
                }else if (key[KEY_DOWN]){
                                yplayer += movelinkby;
                                rereblit = 1;
                                pos = 2;
                }
                if (key[KEY_RIGHT]){
                                xplayer += movelinkby;
                                rereblit = 1;
                                pos = 1;
                }else if (key[KEY_LEFT]){
                                xplayer -= movelinkby;
                                rereblit = 1;
                                pos = 3;
                }
                if (key[KEY_V]){
                                if (envync == 1){
                                                                envync = 0;
                                                                textout_ex(screen, font, "VSync Diabled", 10, 10, makecol(0,0,0),-1);
                                }else{
                                                                envync = 1;
                                                                textout_ex(screen, font, "VSync Enabled", 10, 10, makecol(0,0,0),-1);
                                }
                }
        }

    if (lastbeat != gtimer){
	//The new system forces us to manually poll it.
	al_poll_duh(overworld_player);
    if (rereblit == 1){
        if (envync == 1){
                vsync();
        }
        blit (buffer, screen_buffer, x_scroll, y_scroll, 0, 0, 640, 480);
        if (stand){
                if (pos == 0){
                                draw_rle_sprite(screen_buffer, link_body_stand_north, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_north, xplayer, yplayer);
                }else if (pos == 2){
                                draw_rle_sprite(screen_buffer, link_body_stand_south, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_south, xplayer, yplayer);
                }else if (pos == 1){
                                draw_rle_sprite(screen_buffer, link_body_stand_east, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_east, xplayer, yplayer);
                }else if (pos == 3){
                                draw_rle_sprite(screen_buffer, link_body_stand_west, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_west, xplayer, yplayer);
                }
        }                                
        blit (screen_buffer, screen, 0, 0, 0, 0, 640, 480);

        rereblit = 0;
        clear_keybuf();
    }
    lastbeat = gtimer;
    yield_timeslice();
    }
    }
        
    set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
  cout << "INIT: Closing down internal proceedures." << endl;

	al_stop_duh(overworld_player);
  remove_sound();
  allegro_message ("Thank you for using SoE.");
	dumb_exit();
  allegro_exit();
  cout << "INIT: Goodbye!" << endl;
  return 0;
}

END_OF_MAIN();

```

Note:
I simply commented out the following lines:
```
      if (install_sound(DIGI_AUTODETECT, MIDI_AUTODETECT, argv[0]) != 0) {
           allegro_message("Error initialising sound system\n%s\n", allegro_error);
           return 1;
      }
```

aww man :(

```
joe@joe-laptop:~$ sudo apt-get install libaldmb1-dev
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnuplot gnustep-base-common dvdrip-doc python-pexpect xulrunner-1.9.2
  xulrunner-1.9.3 libavahi-compat-libdnssd1 libevent-execflow-perl
  gnustep-base-runtime groff libnet-ssleay-perl twolame librsvg2-2.18-cil
  gnustep-gui-common libintl-perl libgdata1.4-cil libapm1 transcode-utils
  gnustep-back0.16 transcode-doc transfig libgnustep-gui0.16 mencoder
  subtitleripper gnustep-back0.16-art libxine1-ffmpeg gnuplot-x11
  libevent-rpc-perl ogmtools gtk2-ex-formfactory-perl libgnustep-base1.19
  gnustep-common gnuplot-nox lsdvd vamps libnspr4-dev transcode gnustep-gpbs
  fping netpbm libwnck2.20-cil anyevent-perl sox psutils gocr libevent-perl
  libnetpbm10 mjpegtools gnustep-back-common xine-ui libacpi0 libobjc2
  libio-socket-ssl-perl mkvtoolnix gnustep-gui-runtime libjpeg-progs
  libgnomedesktop2.20-cil libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaldmb1 libdumb1 libdumb1-dev
The following NEW packages will be installed:
  libaldmb1 libaldmb1-dev libdumb1 libdumb1-dev
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 407kB of archives.
After this operation, 1,114kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirror.cc.columbia.edu karmic/universe libdumb1 1:0.9.3-5.1 [194kB]
Get:2 http://mirror.cc.columbia.edu karmic/universe libaldmb1 1:0.9.3-5.1 [94.7kB]
Get:3 http://mirror.cc.columbia.edu karmic/universe libdumb1-dev 1:0.9.3-5.1 [113kB]
Get:4 http://mirror.cc.columbia.edu karmic/universe libaldmb1-dev 1:0.9.3-5.1 [4,946B]
Fetched 407kB in 2s (141kB/s)       
Selecting previously deselected package libdumb1.
(Reading database ... 340050 files and directories currently installed.)
Unpacking libdumb1 (from .../libdumb1_1%3a0.9.3-5.1_i386.deb) ...
Selecting previously deselected package libaldmb1.
Unpacking libaldmb1 (from .../libaldmb1_1%3a0.9.3-5.1_i386.deb) ...
Selecting previously deselected package libdumb1-dev.
Unpacking libdumb1-dev (from .../libdumb1-dev_1%3a0.9.3-5.1_i386.deb) ...
Selecting previously deselected package libaldmb1-dev.
Unpacking libaldmb1-dev (from .../libaldmb1-dev_1%3a0.9.3-5.1_i386.deb) ...
Setting up libdumb1 (1:0.9.3-5.1) ...

Setting up libaldmb1 (1:0.9.3-5.1) ...

Setting up libdumb1-dev (1:0.9.3-5.1) ...
Setting up libaldmb1-dev (1:0.9.3-5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
joe@joe-laptop:~$ '/home/joe/Games/soe-linux-0.2/compile.sh' 
Compiling SoE
g++: main.cpp: No such file or directory
Finished.
joe@joe-laptop:~$ g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
g++: main.cpp: No such file or directory
joe@joe-laptop:~$ sudo g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
g++: main.cpp: No such file or directory
joe@joe-laptop:~$ sudo apt-get install g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
E: Option soeunix: Configuration item specification must have an =<val>.
joe@joe-laptop:~$ 

```

I wanna play :(

---

### Post by KIAaze on 2009-12-16
If you want to play, you first need to get familiar with the command-line. ;)

```
joe@joe-laptop:~$ sudo apt-get install libaldmb1-dev

```
->This command works from any directory because it doesn't work on any local files.

```

joe@joe-laptop:~$ '/home/joe/Games/soe-linux-0.2/compile.sh' 
Compiling SoE
g++: main.cpp: No such file or directory
Finished.

```
No such file or directory is a very clear message. It means it can't find "main.cpp" in the current directory, which in this case is "~"=your home directory.
In this case, the main.cpp file is in the package you downloaded and extracted, so you have to go into that directory before running the command.
('/home/joe/Games/soe-linux-0.2/compile.sh' is a script by the way, i.e. a simple list of commands. Open it in a text editor to get a better idea.)
```

joe@joe-laptop:~$ g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
g++: main.cpp: No such file or directory

```
Same as previously.
```

joe@joe-laptop:~$ sudo g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
g++: main.cpp: No such file or directory

```
Same as previously.
Also: you usually never have to run any "g++" command with "sudo". Using sudo unnecessarily is a bad security practice.
```

joe@joe-laptop:~$ sudo apt-get install g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
E: Option soeunix: Configuration item specification must have an =<val>.

```
This shows that you didn't understand the command line I gave you at all.
Every command begins with a program, eventually followed by arguments (which can also be program names, but are usually not).
In the case of "g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`" the program is "g++".
"g++" is a [compiler]("http://en.wikipedia.org/wiki/Compiler").
"-o soeunix main.cpp -laldmb  `allegro-config --libs`" are all just arguments passed to g++.
So if there is any program you needed to install it would be "g++".

Here are a few links to familiarize yourself with the command-line:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://linuxcommand.org/](http://linuxcommand.org/)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

Happy hacking. :)

And in case you want quick results:
1) Replace "/home/joe/Games/soe-linux-0.2/main.cpp" with the main.cpp I posted previously.
2)
```
cd /home/joe/Games/soe-linux-0.2/
g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
./soeunix

```

---

### Post by steigerjb on 2009-12-17
> **KIAaze said:**
> This shows that you didn't understand the command line I gave you at all.

Happy hacking. :)



Nope, totally lost here. Can't you just post here, **VERY SIMPLY**, what I have to do in the terminal, what I need to do to hack the file,...???

PLEASE! [-o<

---

### Post by KIAaze on 2009-12-17
1) Replace the contents of "/home/joe/Games/soe-linux-0.2/main.cpp" with:
```
/* The Legend Of Zelda: Storms of Evil
    Credits:
        Produced by:
                Adam Cook (a.k.a. Blue Falkon/CC)
        
        Game Programming by:  
                Vectec Software Inc. (http://vectec.net)

        Game Concept by:
                Adam Cook (a.k.a. Blue Falkon/CC)

        Graphics by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Gad Deutcsh (a.k.a. StellarWind Elsydeon)
                Cody Harris
        
        Level Design by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Ruben Sibon (MadMoblin)

        Music compositions by:
                Johnathan Palmer (Morphix)
                Adam Cook (a.k.a. Blue Falkon/CC)

        Special thanks to:

        Zelda is a registered trademark of Nintendo International
    
    Info:
        Storms of evil is a Zelda game built from C++ and allegro, using sheets
        from Open Zelda as well as some custom ones.
        
*/
#include <iostream>
#include <stdlib.h>
#include <string>
#include <fstream>
#include <vector>
#include <cstdlib>

//Ok, lets dynamically load any libraries we need.
#include "modules.h"
#define P_NAME "The Legend of Zelda: Storm of Evil"
#include "outside_tile.h"

BITMAP *linkbuffer;


int convert (BITMAP *todump, char* filename);

int main(int argc, char *argv[])
{
	//Titlescreen Music
	MIDI *the_music;

	//Buffer
	char buf[256];

	//Outside sheet Init
	BITMAP *tile_buffer;
	BITMAP *buffer;
	BITMAP *screen_buffer;
    
	//Default File:
	string szfile("soelevel.txt");
   	string szline;
	cout << "INIT: IDENT: LOZSOE" << endl;
	cout << "INIT: Internel program name: " << P_NAME << endl;
	cout << "INIT: Starting intenal proceedures." << endl;
	if (allegro_init()){
		cout << "INIT: Unable to load Allgero!" << endl;
		return 1;
	}


	//DUMB INIT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
	//atexit(&dumb_exit);
	dumb_register_stdfiles();
	dumb_register_packfiles();



	set_window_title("SoE: INIT");
	if(install_timer()){
		cout << "INIT: Error installing timer." << endl;
		return 1;
	}
	install_keyboard(); 


     
     //timer related stuff
     LOCK_VARIABLE(gtimer);
     LOCK_FUNCTION(gamtimer);
     install_int_ex(gametimer, BPS_TO_TIMER(80));

//      if (install_sound(DIGI_AUTODETECT, MIDI_AUTODETECT, argv[0]) != 0) {
//           allegro_message("Error initialising sound system\n%s\n", allegro_error);
//           return 1;
//      }


    cout << "INIT: Ready to launch core." << endl;
    if (desktop_color_depth() < 8){
        cout << "This game requires at least 15 bit colour depth." << endl;
        return 1;
    }else{
        cout << "INIT: Color Depth OK (" << desktop_color_depth() << ")" << endl;
    }
    set_color_depth(24);
    
    if (set_gfx_mode(GFX_AUTODETECT_WINDOWED, 640, 480, 0, 0)){
        cout << "INIT: Error setting res. Attempted windowed." << endl;
        system ("pause");
        return 1; 
    }
    clear_to_color(screen, makecol(127, 127, 255));
    //text_mode(-1);
    textout_centre_ex(screen, font, "Please Wait", SCREEN_W/2, SCREEN_H/2 - 20, makecol(255,255,255), -1);
    textout_centre_ex(screen, font, "SoE is Loading...This may take a while", SCREEN_W/2, SCREEN_H/2 + 20, makecol(255,255,255), -1);
    cout << "INIT: Loading Datafile: ";
     if((soe_datafile=load_datafile("soe.dat"))==NULL) {
          cout << "Error loading soe.dat" << endl;
          system ("PAUSE");
          exit(1);
     }
     cout << " OK" << endl;
     the_music = (MIDI *)soe_datafile[soe_title].dat;
     if (!the_music) {
          allegro_message("Error reading MIDI file '%s'\n", argv[1]);
          return 1;
      }
     cout << "INIT: MIDI Set up and ready!" << endl;
	if (midi_driver){
		cout << "INIT: Music Driver: " << midi_driver->name << endl;
	}
    tilesheet2 osheet1((BITMAP *)soe_datafile[soe_os1].dat);
    tilesheet2 playsheet1((BITMAP *)soe_datafile[soe_playsheet1].dat);
    tilesheet2 soelogo((BITMAP *)soe_datafile[soe_logo].dat);
    tilesheet2 bglayer((BITMAP *)soe_datafile[soe_bglayer].dat);
    int y;
    int x;
    set_window_title("SoE: Welcome to SoE");
	cout << "Loading Intro..." << endl;
#include "intro.h"


    osheet1.settileindexoffset (8,0);
    tile_buffer = osheet1.retbitmaptileindex(11,1);
    
    if (!tile_buffer){
        cout << "ERROR!" << tile_buffer->h << endl;
    }
    //Create screen buffer to remove ugly generation
    buffer = create_bitmap(800, 600);
    screen_buffer = create_bitmap (640, 480);
    linkbuffer = create_bitmap (16,24);

    //for (x = 0; x < 800; x += 16){
    //    for (y = 0; y < 600; y += 16){
    //            blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
    //    }
    //}
    //for (x = 2; x < 38; x++){
    //    draw_tile_grid(osheet1.retbitmaptileindex(8,0), buffer, x, 8);
    //}
        //draw_tile_grid(osheet1.retbitmaptileindex(11,0), buffer, 45, 10);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,1), buffer, 45, 11);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,2), buffer, 45, 12);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,3), buffer, 45, 13);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,4), buffer, 45, 14);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,5), buffer, 45, 15);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,6), buffer, 45, 16);
    int runninggame = 0;

    lastbeat = gtimer;
    int xplayer = 32;
    int yplayer = 32;
    int x_scroll = 0;
    int y_scroll = 0;
    int rereblit = 1;
    rect(buffer, 0, 0, 799, 599, 0);

    //SPRITE DECS
        //BODY
    RLE_SPRITE *link_body_stand_south;
    RLE_SPRITE *link_body_stand_north;
    RLE_SPRITE *link_body_stand_east;
    RLE_SPRITE *link_body_stand_west;

        //HEAD
    RLE_SPRITE *link_head_look_south;
    RLE_SPRITE *link_head_look_north;
    RLE_SPRITE *link_head_look_east;
    RLE_SPRITE *link_head_look_west;

    //SPIRTE MAKES
        //BODY
    link_body_stand_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,1));
    link_body_stand_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,1));
    link_body_stand_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,1));
    link_body_stand_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,1));

        //HEAD    
    link_head_look_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,0));
    link_head_look_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,0));
    link_head_look_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,0));
    link_head_look_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,0));

    clear_to_color(linkbuffer, makecol(255, 0, 255));    
    draw_rle_sprite(linkbuffer, link_body_stand_south, 0, 8);
    draw_rle_sprite(linkbuffer, link_head_look_south, 0, 0);
    int whichscreen = 0;
    int movelinkby = 2;
    int pos = 2;
    int stand = 1;
    int envync = 0;
    set_window_title("SoE: Testbed # 1");


	//Shiney new IT support!
	AL_DUH_PLAYER *overworld_player;
	DUMBFILE *overworld_file;
	DUH *overworld_duh;
	overworld_file = dumbfile_open_memory((char*)soe_datafile[soe_overworld].dat, soe_datafile[soe_title_track].size);
	overworld_duh = dumb_read_it(overworld_file);
	overworld_player = al_start_duh(overworld_duh, 2, 0, 1.0f, get_config_int("sound", "buffer_size", 4096), get_config_int("sound", "sound_freq", 44100));

    //OLD WAV SUPPORT
    //play_sample((SAMPLE *)soe_datafile[soe_overworld].dat, 255, 127, 1000, 1);

    //OLD MIDI SUPPORT
    //play_midi((MIDI *)soe_datafile[soe_lightover].dat, TRUE);

        int linenum = 0;
        int binnum = 0;
        char xx;
        int nchar = 0;
        int xtilecoord = 0;
        int ytilecoord = 0;
    	fstream startf(szfile.c_str(), ios_base::in);
    	if (!startf){
		    	cout << "INIT [FATAL]: File not found" << endl;
		    	return 1;
    	}
	cout << "INIT: Opened " << szfile.c_str() << " for reading." << endl;
    	while (!startf.eof()){
			startf.get(xx);
			if (xx == '\n'){
		    		linenum++;
		    		if (linenum == 1){
                        		binnum = atoi(szline.c_str());
					xtilecoord = (binnum & 15872) / 512;
					ytilecoord = (binnum & 496) / 16;
					osheet1.settileindexoffset (8,0);
					tile_buffer = osheet1.retbitmaptileindex(xtilecoord,ytilecoord);
					for (x = 0; x < 800; x += 16){
						for (y = 0; y < 600; y += 16){
							blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
						}
					}
				}else{
					cout << "Ignoring Line: " << linenum << endl;
				}
				
				nchar = 0;
				szline.erase();
			}else{
				szline += xx;
				nchar++;
			}
	}


    while (runninggame == 0){
    yield_timeslice();
        if (keypressed()){
                k = readkey();
                if (key[KEY_ESC]){
                                cout << "ENDING GAME" << endl;
                                runninggame = 1;
                }
                if (key[KEY_UP]){
                                yplayer -= movelinkby;
                                rereblit = 1;
                                pos = 0;
                }else if (key[KEY_DOWN]){
                                yplayer += movelinkby;
                                rereblit = 1;
                                pos = 2;
                }
                if (key[KEY_RIGHT]){
                                xplayer += movelinkby;
                                rereblit = 1;
                                pos = 1;
                }else if (key[KEY_LEFT]){
                                xplayer -= movelinkby;
                                rereblit = 1;
                                pos = 3;
                }
                if (key[KEY_V]){
                                if (envync == 1){
                                                                envync = 0;
                                                                textout_ex(screen, font, "VSync Diabled", 10, 10, makecol(0,0,0),-1);
                                }else{
                                                                envync = 1;
                                                                textout_ex(screen, font, "VSync Enabled", 10, 10, makecol(0,0,0),-1);
                                }
                }
        }

    if (lastbeat != gtimer){
	//The new system forces us to manually poll it.
	al_poll_duh(overworld_player);
    if (rereblit == 1){
        if (envync == 1){
                vsync();
        }
        blit (buffer, screen_buffer, x_scroll, y_scroll, 0, 0, 640, 480);
        if (stand){
                if (pos == 0){
                                draw_rle_sprite(screen_buffer, link_body_stand_north, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_north, xplayer, yplayer);
                }else if (pos == 2){
                                draw_rle_sprite(screen_buffer, link_body_stand_south, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_south, xplayer, yplayer);
                }else if (pos == 1){
                                draw_rle_sprite(screen_buffer, link_body_stand_east, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_east, xplayer, yplayer);
                }else if (pos == 3){
                                draw_rle_sprite(screen_buffer, link_body_stand_west, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_west, xplayer, yplayer);
                }
        }                                
        blit (screen_buffer, screen, 0, 0, 0, 0, 640, 480);

        rereblit = 0;
        clear_keybuf();
    }
    lastbeat = gtimer;
    yield_timeslice();
    }
    }
        
    set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
  cout << "INIT: Closing down internal proceedures." << endl;

	al_stop_duh(overworld_player);
  remove_sound();
  allegro_message ("Thank you for using SoE.");
	dumb_exit();
  allegro_exit();
  cout << "INIT: Goodbye!" << endl;
  return 0;
}

END_OF_MAIN();
```

2) Run the following commands:
```

sudo apt-get install build-essential libaldmb1-dev
cd /home/joe/Games/soe-linux-0.2/
g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
./soeunix

```

---

### Post by steigerjb on 2009-12-19
> **KIAaze said:**
> 1) Replace the contents of "/home/joe/Games/soe-linux-0.2/main.cpp" with:
```
/* The Legend Of Zelda: Storms of Evil
    Credits:
        Produced by:
                Adam Cook (a.k.a. Blue Falkon/CC)
        
        Game Programming by:  
                Vectec Software Inc. (http://vectec.net)

        Game Concept by:
                Adam Cook (a.k.a. Blue Falkon/CC)

        Graphics by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Gad Deutcsh (a.k.a. StellarWind Elsydeon)
                Cody Harris
        
        Level Design by:
                Adam Cook (a.k.a. Blue Falkon/CC)
                Ruben Sibon (MadMoblin)

        Music compositions by:
                Johnathan Palmer (Morphix)
                Adam Cook (a.k.a. Blue Falkon/CC)

        Special thanks to:

        Zelda is a registered trademark of Nintendo International
    
    Info:
        Storms of evil is a Zelda game built from C++ and allegro, using sheets
        from Open Zelda as well as some custom ones.
        
*/
#include <iostream>
#include <stdlib.h>
#include <string>
#include <fstream>
#include <vector>
#include <cstdlib>

//Ok, lets dynamically load any libraries we need.
#include "modules.h"
#define P_NAME "The Legend of Zelda: Storm of Evil"
#include "outside_tile.h"

BITMAP *linkbuffer;


int convert (BITMAP *todump, char* filename);

int main(int argc, char *argv[])
{
	//Titlescreen Music
	MIDI *the_music;

	//Buffer
	char buf[256];

	//Outside sheet Init
	BITMAP *tile_buffer;
	BITMAP *buffer;
	BITMAP *screen_buffer;
    
	//Default File:
	string szfile("soelevel.txt");
   	string szline;
	cout << "INIT: IDENT: LOZSOE" << endl;
	cout << "INIT: Internel program name: " << P_NAME << endl;
	cout << "INIT: Starting intenal proceedures." << endl;
	if (allegro_init()){
		cout << "INIT: Unable to load Allgero!" << endl;
		return 1;
	}


	//DUMB INIT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
	//atexit(&dumb_exit);
	dumb_register_stdfiles();
	dumb_register_packfiles();



	set_window_title("SoE: INIT");
	if(install_timer()){
		cout << "INIT: Error installing timer." << endl;
		return 1;
	}
	install_keyboard(); 


     
     //timer related stuff
     LOCK_VARIABLE(gtimer);
     LOCK_FUNCTION(gamtimer);
     install_int_ex(gametimer, BPS_TO_TIMER(80));

//      if (install_sound(DIGI_AUTODETECT, MIDI_AUTODETECT, argv[0]) != 0) {
//           allegro_message("Error initialising sound system\n%s\n", allegro_error);
//           return 1;
//      }


    cout << "INIT: Ready to launch core." << endl;
    if (desktop_color_depth() < 8){
        cout << "This game requires at least 15 bit colour depth." << endl;
        return 1;
    }else{
        cout << "INIT: Color Depth OK (" << desktop_color_depth() << ")" << endl;
    }
    set_color_depth(24);
    
    if (set_gfx_mode(GFX_AUTODETECT_WINDOWED, 640, 480, 0, 0)){
        cout << "INIT: Error setting res. Attempted windowed." << endl;
        system ("pause");
        return 1; 
    }
    clear_to_color(screen, makecol(127, 127, 255));
    //text_mode(-1);
    textout_centre_ex(screen, font, "Please Wait", SCREEN_W/2, SCREEN_H/2 - 20, makecol(255,255,255), -1);
    textout_centre_ex(screen, font, "SoE is Loading...This may take a while", SCREEN_W/2, SCREEN_H/2 + 20, makecol(255,255,255), -1);
    cout << "INIT: Loading Datafile: ";
     if((soe_datafile=load_datafile("soe.dat"))==NULL) {
          cout << "Error loading soe.dat" << endl;
          system ("PAUSE");
          exit(1);
     }
     cout << " OK" << endl;
     the_music = (MIDI *)soe_datafile[soe_title].dat;
     if (!the_music) {
          allegro_message("Error reading MIDI file '%s'\n", argv[1]);
          return 1;
      }
     cout << "INIT: MIDI Set up and ready!" << endl;
	if (midi_driver){
		cout << "INIT: Music Driver: " << midi_driver->name << endl;
	}
    tilesheet2 osheet1((BITMAP *)soe_datafile[soe_os1].dat);
    tilesheet2 playsheet1((BITMAP *)soe_datafile[soe_playsheet1].dat);
    tilesheet2 soelogo((BITMAP *)soe_datafile[soe_logo].dat);
    tilesheet2 bglayer((BITMAP *)soe_datafile[soe_bglayer].dat);
    int y;
    int x;
    set_window_title("SoE: Welcome to SoE");
	cout << "Loading Intro..." << endl;
#include "intro.h"


    osheet1.settileindexoffset (8,0);
    tile_buffer = osheet1.retbitmaptileindex(11,1);
    
    if (!tile_buffer){
        cout << "ERROR!" << tile_buffer->h << endl;
    }
    //Create screen buffer to remove ugly generation
    buffer = create_bitmap(800, 600);
    screen_buffer = create_bitmap (640, 480);
    linkbuffer = create_bitmap (16,24);

    //for (x = 0; x < 800; x += 16){
    //    for (y = 0; y < 600; y += 16){
    //            blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
    //    }
    //}
    //for (x = 2; x < 38; x++){
    //    draw_tile_grid(osheet1.retbitmaptileindex(8,0), buffer, x, 8);
    //}
        //draw_tile_grid(osheet1.retbitmaptileindex(11,0), buffer, 45, 10);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,1), buffer, 45, 11);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,2), buffer, 45, 12);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,3), buffer, 45, 13);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,4), buffer, 45, 14);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,5), buffer, 45, 15);
        //draw_tile_grid(osheet1.retbitmaptileindex(11,6), buffer, 45, 16);
    int runninggame = 0;

    lastbeat = gtimer;
    int xplayer = 32;
    int yplayer = 32;
    int x_scroll = 0;
    int y_scroll = 0;
    int rereblit = 1;
    rect(buffer, 0, 0, 799, 599, 0);

    //SPRITE DECS
        //BODY
    RLE_SPRITE *link_body_stand_south;
    RLE_SPRITE *link_body_stand_north;
    RLE_SPRITE *link_body_stand_east;
    RLE_SPRITE *link_body_stand_west;

        //HEAD
    RLE_SPRITE *link_head_look_south;
    RLE_SPRITE *link_head_look_north;
    RLE_SPRITE *link_head_look_east;
    RLE_SPRITE *link_head_look_west;

    //SPIRTE MAKES
        //BODY
    link_body_stand_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,1));
    link_body_stand_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,1));
    link_body_stand_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,1));
    link_body_stand_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,1));

        //HEAD    
    link_head_look_south = get_rle_sprite(playsheet1.retbitmaptileindex(2,0));
    link_head_look_north = get_rle_sprite(playsheet1.retbitmaptileindex(3,0));
    link_head_look_west = get_rle_sprite(playsheet1.retbitmaptileindex(1,0));
    link_head_look_east = get_rle_sprite(playsheet1.retbitmaptileindex(0,0));

    clear_to_color(linkbuffer, makecol(255, 0, 255));    
    draw_rle_sprite(linkbuffer, link_body_stand_south, 0, 8);
    draw_rle_sprite(linkbuffer, link_head_look_south, 0, 0);
    int whichscreen = 0;
    int movelinkby = 2;
    int pos = 2;
    int stand = 1;
    int envync = 0;
    set_window_title("SoE: Testbed # 1");


	//Shiney new IT support!
	AL_DUH_PLAYER *overworld_player;
	DUMBFILE *overworld_file;
	DUH *overworld_duh;
	overworld_file = dumbfile_open_memory((char*)soe_datafile[soe_overworld].dat, soe_datafile[soe_title_track].size);
	overworld_duh = dumb_read_it(overworld_file);
	overworld_player = al_start_duh(overworld_duh, 2, 0, 1.0f, get_config_int("sound", "buffer_size", 4096), get_config_int("sound", "sound_freq", 44100));

    //OLD WAV SUPPORT
    //play_sample((SAMPLE *)soe_datafile[soe_overworld].dat, 255, 127, 1000, 1);

    //OLD MIDI SUPPORT
    //play_midi((MIDI *)soe_datafile[soe_lightover].dat, TRUE);

        int linenum = 0;
        int binnum = 0;
        char xx;
        int nchar = 0;
        int xtilecoord = 0;
        int ytilecoord = 0;
    	fstream startf(szfile.c_str(), ios_base::in);
    	if (!startf){
		    	cout << "INIT [FATAL]: File not found" << endl;
		    	return 1;
    	}
	cout << "INIT: Opened " << szfile.c_str() << " for reading." << endl;
    	while (!startf.eof()){
			startf.get(xx);
			if (xx == '\n'){
		    		linenum++;
		    		if (linenum == 1){
                        		binnum = atoi(szline.c_str());
					xtilecoord = (binnum & 15872) / 512;
					ytilecoord = (binnum & 496) / 16;
					osheet1.settileindexoffset (8,0);
					tile_buffer = osheet1.retbitmaptileindex(xtilecoord,ytilecoord);
					for (x = 0; x < 800; x += 16){
						for (y = 0; y < 600; y += 16){
							blit(tile_buffer, buffer, 0, 0, x, y, 16, 16);
						}
					}
				}else{
					cout << "Ignoring Line: " << linenum << endl;
				}
				
				nchar = 0;
				szline.erase();
			}else{
				szline += xx;
				nchar++;
			}
	}


    while (runninggame == 0){
    yield_timeslice();
        if (keypressed()){
                k = readkey();
                if (key[KEY_ESC]){
                                cout << "ENDING GAME" << endl;
                                runninggame = 1;
                }
                if (key[KEY_UP]){
                                yplayer -= movelinkby;
                                rereblit = 1;
                                pos = 0;
                }else if (key[KEY_DOWN]){
                                yplayer += movelinkby;
                                rereblit = 1;
                                pos = 2;
                }
                if (key[KEY_RIGHT]){
                                xplayer += movelinkby;
                                rereblit = 1;
                                pos = 1;
                }else if (key[KEY_LEFT]){
                                xplayer -= movelinkby;
                                rereblit = 1;
                                pos = 3;
                }
                if (key[KEY_V]){
                                if (envync == 1){
                                                                envync = 0;
                                                                textout_ex(screen, font, "VSync Diabled", 10, 10, makecol(0,0,0),-1);
                                }else{
                                                                envync = 1;
                                                                textout_ex(screen, font, "VSync Enabled", 10, 10, makecol(0,0,0),-1);
                                }
                }
        }

    if (lastbeat != gtimer){
	//The new system forces us to manually poll it.
	al_poll_duh(overworld_player);
    if (rereblit == 1){
        if (envync == 1){
                vsync();
        }
        blit (buffer, screen_buffer, x_scroll, y_scroll, 0, 0, 640, 480);
        if (stand){
                if (pos == 0){
                                draw_rle_sprite(screen_buffer, link_body_stand_north, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_north, xplayer, yplayer);
                }else if (pos == 2){
                                draw_rle_sprite(screen_buffer, link_body_stand_south, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_south, xplayer, yplayer);
                }else if (pos == 1){
                                draw_rle_sprite(screen_buffer, link_body_stand_east, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_east, xplayer, yplayer);
                }else if (pos == 3){
                                draw_rle_sprite(screen_buffer, link_body_stand_west, xplayer, yplayer + 8);
                                draw_rle_sprite(screen_buffer, link_head_look_west, xplayer, yplayer);
                }
        }                                
        blit (screen_buffer, screen, 0, 0, 0, 0, 640, 480);

        rereblit = 0;
        clear_keybuf();
    }
    lastbeat = gtimer;
    yield_timeslice();
    }
    }
        
    set_gfx_mode(GFX_TEXT, 0, 0, 0, 0);
  cout << "INIT: Closing down internal proceedures." << endl;

	al_stop_duh(overworld_player);
  remove_sound();
  allegro_message ("Thank you for using SoE.");
	dumb_exit();
  allegro_exit();
  cout << "INIT: Goodbye!" << endl;
  return 0;
}

END_OF_MAIN();
```

2) Run the following commands:
```

sudo apt-get install build-essential libaldmb1-dev
cd /home/joe/Games/soe-linux-0.2/
g++ -o soeunix main.cpp -laldmb  `allegro-config --libs`
./soeunix

```

i got what you said b4. got the start screen but then link on a green screen :(

---

### Post by steigerjb on 2009-12-31
> **steigerjb said:**
> i got what you said b4. got the start screen but then link on a green screen :(

bump

---

### Post by KIAaze on 2010-01-01
That's what I said earlier. There currently doesn't seem to be any more content than that.
It's still in a pre-alpha status despite the nice website promising a superb game. (and it looks like it has been abandoned too)

If you want to play Zelda under Ubuntu, I recommend installing ZSNES:
```
sudo apt-get install zsnes
```
And playing "Zelda: A link to the past" by loading the ROM image which is available here:
[http://www.coolrom.com/roms/snes/7976/Zelda_-_A_Link_to_the_Past.php](http://www.coolrom.com/roms/snes/7976/Zelda_-_A_Link_to_the_Past.php) (using ROMs is illegal unless you own the original game by the way (AFAIK))
(It's a .zip file, so you need to unzip it first)

Otherwise, if you are interested in open-source zelda games:
[http://sourceforge.net/projects/openzelda/](http://sourceforge.net/projects/openzelda/)
[http://www.zeldauniverse.net/forums/general-zelda/41687-open-source-glzelda.html](http://www.zeldauniverse.net/forums/general-zelda/41687-open-source-glzelda.html)
[http://openlynks.sourceforge.net/](http://openlynks.sourceforge.net/)

Head to the Gaming&Leisure section of this forum if you want more game suggestions.

---

### Post by steigerjb on 2010-01-01
> **KIAaze said:**
> That's what I said earlier. There currently doesn't seem to be any more content than that.
It's still in a pre-alpha status despite the nice website promising a superb game. (and it looks like it has been abandoned too)

If you want to play Zelda under Ubuntu, I recommend installing ZSNES:
```
sudo apt-get install zsnes
```
And playing "Zelda: A link to the past" by loading the ROM image which is available here:
[http://www.coolrom.com/roms/snes/7976/Zelda_-_A_Link_to_the_Past.php](http://www.coolrom.com/roms/snes/7976/Zelda_-_A_Link_to_the_Past.php) (using ROMs is illegal unless you own the original game by the way (AFAIK))
(It's a .zip file, so you need to unzip it first)

Otherwise, if you are interested in open-source zelda games:
[http://sourceforge.net/projects/openzelda/](http://sourceforge.net/projects/openzelda/)
[http://www.zeldauniverse.net/forums/general-zelda/41687-open-source-glzelda.html](http://www.zeldauniverse.net/forums/general-zelda/41687-open-source-glzelda.html)
[http://openlynks.sourceforge.net/](http://openlynks.sourceforge.net/)

Head to the Gaming&Leisure section of this forum if you want more game suggestions.

alright, I'll try those open source zelda games. I already have the roms.

---

### Post by JimInLakeland on 2010-01-01
> **Maheriano said:**
> So they're using the game names without permission?

Since the author is not trying to prosper using the name, Nintendo will probably not worry about it. It falls in the realm of "fan" related content.

---

