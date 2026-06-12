---
title: "Analogue Clock screen saver for Ubuntu"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by machdohvah on 2011-05-10
I wish someone would create a screen saver with a great big analogue clock for Ubunutu 10.10 See the following C++ code that I built for DOS long ago.

```
// ACLOCK.CPP (modified last 14Aug2010) 
 
/* 
 
Produces an analog clock on the screen. 
 
14Aug2010 Program a date checking sequence at 00:01:00 am 
 
*/ 
 
#define DELAY_SECTION 
 
#include <conio.h> 
#include <dos.h> 
#include <graphics.h> 
#include <stdio.h> 
#include <stdlib.h> 
#include <time.h> 
 
struct dostime_t gTime; 
struct tm *time_now; 
time_t secs_now; 
 
void StartOver(); 
 
int gDriver = DETECT, gMode, gError; 
int gMidX, gMidY; 
int gAlarmRequested = 0, gAlarmHour = 12, gAlarmMinute = 0; 
int gSecondHand, gMinuteHand, gHourHand; 
int gSecondSave, gMinuteSave, gHourSave; 
int gSecondDegree = 0, gMinuteDegree = 0, gHourDegree = 0; 
char s[80] = ""; 
 
void main(int argc, char **argv) { 
  int i; 
 
  if (argc >= 2) { 
    for (i=1;i<argc;i++) { 
      if ((argv[i][0] == '/') || (argv[i][0] == '-')) { 
        switch (argv[i][1]) { 
/* 
 
Help section 
 
*/ 
        case '?': 
          printf("\nACLOCK [-aHH:MM]\n\n"); 
          printf("-a = Set alarm to sound at HH:MM military time\n"); 
          printf("HH = 00-23\n"); 
          printf("MM = 00-59\n"); 
          exit( 1 ); 
          break; 
/* 
 
Alarm settings 
 
*/ 
        case 'A': 
        case 'a': 
          gAlarmRequested = 1; 
          s[0] = argv[1][2]; s[1] = argv[1][3]; s[2] = 0x00; 
          gAlarmHour = atoi(s); 
          s[0] = argv[1][5]; s[1] = argv[1][6]; s[2] = 0x00; 
          gAlarmMinute = atoi(s); 
          if (gAlarmHour < 0) gAlarmHour =  0; 
          if (gAlarmHour >23) gAlarmHour = 23; 
          if (gAlarmMinute < 0) gAlarmMinute =  0; 
          if (gAlarmMinute >59) gAlarmMinute = 59; 
          break; 
        } 
      } 
    } 
  } 
/* 
 
Initialize graphics 
 
*/ 
  initgraph(&gDriver, &gMode, "C:\\TC\\BGI"); 
  gError = graphresult(); 
  if (gError != grOk) { 
    printf("Graphics error: %s\n", grapherrormsg(gError)); 
    exit(1); 
  } 
  gMidX = getmaxx() / 2; 
  gMidY = getmaxy() / 2; 
  gSecondHand = (int) (gMidY * .95); 
  gMinuteHand = (int) (gMidY * .80); 
  gHourHand = (int) (gMidY * .50); 
/* 
 
Show date 
 
*/ 
  tzset(); 
  StartOver(); 
 
/* 
 
Main loop 
 
*/ 
  while (!kbhit()) { 
    gHourSave = gHourDegree; 
    gMinuteSave = gMinuteDegree; 
    gSecondSave = gSecondDegree; 
    _dos_gettime(&gTime); 
/* 
 
Re-init section 
 
*/ 
    if ((gTime.hour   == 0) && 
        (gTime.minute == 0) && 
        (gTime.second == 1)) { 
      cleardevice(); 
      StartOver(); 
    } 
/* 
 
Alarm section 
 
*/ 
    if (gAlarmRequested) { 
      if ((gTime.hour   == gAlarmHour  ) && 
          (gTime.minute == gAlarmMinute) && 
          (gTime.second == 0           )) 
        sound(440); 
      if ((gTime.hour   == gAlarmHour  ) && 
          (gTime.minute == gAlarmMinute) && 
          (gTime.second == 5           )) 
        nosound(); 
    } 
/* 
 
Calculate hours, minutes, seconds, angles 
 
*/ 
    gHourDegree = (810-(((unsigned int) ((gTime.hour%12)*3600) 
      +(unsigned int) (gTime.minute*60)+gTime.second)/120))%360; 
    gMinuteDegree = (810-((gTime.minute*60+gTime.second)/10))%360; 
    gSecondDegree = (810-(gTime.second*6+(int)(gTime.hsecond*.06)))%360; 
    if (gHourDegree == 0) gHourDegree = 360; 
    if (gMinuteDegree == 0) gMinuteDegree = 360; 
    if (gSecondDegree == 0) gSecondDegree = 360; 
/* 
 
Second hand 
 
*/ 
    setfillstyle(EMPTY_FILL, BLACK); 
    setcolor(BLACK); 
    pieslice(gMidX, gMidY, gSecondSave, gSecondSave+1, gSecondHand); 
    setcolor(LIGHTRED); 
    pieslice(gMidX, gMidY, gSecondDegree, gSecondDegree+1, gSecondHand); 
    setcolor(BLACK); 
    pieslice(gMidX, gMidY, gSecondDegree+1, gSecondDegree+2, gSecondHand); 
/* 
 
Draw numbers on clock face 
 
*/ 
    setcolor(YELLOW); 
    outtextxy(gMidX + (int) (gMidX*.32), gMidY - (int) (gMidY*.82), "1"); 
    outtextxy(gMidX + (int) (gMidX*.58), gMidY - (int) (gMidY*.50), "2"); 
    outtextxy(gMidX + (int) (gMidX*.68), gMidY - (int) (gMidY*.01), "3"); 
    outtextxy(gMidX + (int) (gMidX*.58), gMidY + (int) (gMidY*.45), "4"); 
    outtextxy(gMidX + (int) (gMidX*.32), gMidY + (int) (gMidY*.80), "5"); 
    outtextxy(gMidX - (int) (gMidX*.01), gMidY + (int) (gMidY*.92), "6"); 
    outtextxy(gMidX - (int) (gMidX*.35), gMidY + (int) (gMidY*.80), "7"); 
    outtextxy(gMidX - (int) (gMidX*.60), gMidY + (int) (gMidY*.45), "8"); 
    outtextxy(gMidX - (int) (gMidX*.70), gMidY - (int) (gMidY*.01), "9"); 
    outtextxy(gMidX - (int) (gMidX*.60), gMidY - (int) (gMidY*.47), "10"); 
    outtextxy(gMidX - (int) (gMidX*.35), gMidY - (int) (gMidY*.82), "11"); 
    outtextxy(gMidX - (int) (gMidX*.01), gMidY - (int) (gMidY*.95), "12"); 
/* 
 
Minute hand 
 
*/ 
    if (gMinuteSave != gMinuteDegree) { 
      setcolor(BLACK); 
      pieslice(gMidX-2, gMidY, gMinuteSave, gMinuteSave+1, gMinuteHand); 
      pieslice(gMidX+2, gMidY, gMinuteSave, gMinuteSave+1, gMinuteHand); 
      pieslice(gMidX, gMidY-2, gMinuteSave, gMinuteSave+1, gMinuteHand); 
      pieslice(gMidX, gMidY+2, gMinuteSave, gMinuteSave+1, gMinuteHand); 
      pieslice(gMidX,   gMidY, gMinuteSave, gMinuteSave+1, gMinuteHand); 
    } 
    setcolor(YELLOW); 
    pieslice(gMidX-2, gMidY, gMinuteDegree, gMinuteDegree+1, gMinuteHand); 
    pieslice(gMidX+2, gMidY, gMinuteDegree, gMinuteDegree+1, gMinuteHand); 
    pieslice(gMidX, gMidY-2, gMinuteDegree, gMinuteDegree+1, gMinuteHand); 
    pieslice(gMidX, gMidY+2, gMinuteDegree, gMinuteDegree+1, gMinuteHand); 
    pieslice(gMidX,   gMidY, gMinuteDegree, gMinuteDegree+1, gMinuteHand); 
/* 
 
Hour hand 
 
*/ 
    if (gHourSave != gHourDegree) { 
      setcolor(BLACK); 
      pieslice(gMidX-4, gMidY, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX-2, gMidY, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX+2, gMidY, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX+4, gMidY, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX, gMidY-4, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX, gMidY-2, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX, gMidY+2, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX, gMidY+4, gHourSave, gHourSave+1, gHourHand); 
      pieslice(gMidX,   gMidY, gHourSave, gHourSave+1, gHourHand); 
    } 
    setcolor(YELLOW); 
    pieslice(gMidX-4, gMidY, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX-2, gMidY, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX+2, gMidY, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX+4, gMidY, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX, gMidY-4, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX, gMidY-2, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX, gMidY+2, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX, gMidY+4, gHourDegree, gHourDegree+1, gHourHand); 
    pieslice(gMidX,   gMidY, gHourDegree, gHourDegree+1, gHourHand); 
/* 
 
Wait 1 second 
 
*/ 
#ifdef DELAY_SECTION 
    delay(1000); 
#endif 
  } 
/* 
 
Exit 
 
*/ 
  closegraph(); 
  textmode(C4350); 
  clrscr(); 
} 
 
void StartOver() { 
  int i; 
 
  time( &secs_now ); 
  time_now = localtime( &secs_now ); 
  setcolor(YELLOW); 
  strftime( s, 80, "%a %d %b %Y", time_now ); 
  settextstyle(0, 0, 2); 
  settextjustify(LEFT_TEXT,TOP_TEXT); 
  outtext( s ); 
/* 
 
Clock face tics and circle 
 
*/ 
  setcolor(WHITE); 
  circle(gMidX, gMidY, gMidY); 
  setfillstyle(SOLID_FILL, BLACK); 
  for (i=0;i<360;i+=6) pieslice(gMidX, gMidY, i, i+6, gMidY); 
  setfillstyle(EMPTY_FILL, WHITE); 
  for (i=0;i<360;i+=6) pieslice(gMidX, gMidY, i, i+6, gMidY); 
  setcolor(BLACK); setfillstyle(SOLID_FILL, BLACK); 
  pieslice(gMidX, gMidY, 0, 360, (int) (gMidY * .95)); 
  settextstyle(GOTHIC_FONT, HORIZ_DIR, 4); 
  settextjustify(CENTER_TEXT,CENTER_TEXT); 
}
```

---

### Post by gmargo on 2011-05-10
The KDE screensavers include an analog clock.  But that doesn't help much if you're using Gnome.  The "gltext" screen saver can be configured to give a digital time.

Here's one for gnome (untested). [http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html](http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html)

Found through bug report: [https://bugs.launchpad.net/gnome-screensaver/+bug/46548](https://bugs.launchpad.net/gnome-screensaver/+bug/46548)

---

### Post by machdohvah on 2011-05-10
> **gmargo said:**
> The KDE screensavers include an analog clock.  But that doesn't help much if you're using Gnome.  The "gltext" screen saver can be configured to give a digital time.

Here's one for gnome (untested). [http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html]("http://www.d8.dion.ne.jp/%7Ept2k/software/gnome-clock-screensaver/index_e.html")

Found through bug report: [https://bugs.launchpad.net/gnome-screensaver/+bug/46548](https://bugs.launchpad.net/gnome-screensaver/+bug/46548)

So, I am to understand that this issue was visited before, but dropped because a bug? It is now on my wish list that this program become available for Ubuntu 10.10 as a screen saver ready for installation through Ubuntu Software Center. ty.

Incidentally, I tried to configure "gltext" screen saver and noticed that I am not able to configure any screen saver. A liitle help please?

---

### Post by gmargo on 2011-05-11
> So, I am to understand that this issue was visited before, but dropped because a bug?I think it was evaluated to be just a wishlist thing, not an actual bug.

> Incidentally, I tried to configure "gltext" screen saver and noticed  that I am not able to configure any screen saver. A liitle help  please?Wow, I'm looking around and can't find any configuration dialogs for any of the screensavers under 10.10 Maverick Gnome.  Which is weird because a lot of them have configurable parameters (see **/usr/share/xscreensaver/config/*.xml**).

Quick and dirty method:  Edit the file **/usr/share/applications/screensavers/gltext.desktop**

Modify the "Exec=" line to be:
```

Exec=/usr/lib/xscreensaver/gltext -root -text '%A%n%d %b %Y%n%r'

```See the **strftime(3)** man page for all the potential "%" strings.

---

### Post by wapicke on 2012-11-01
I'm sure the moderators will lock this thread, after this post, as usual, but here goes.  The default screensaver for Gnome doesn't seem to allow editing of screensaver settings.  However, by installing xscreensaver, opening it's control, by the same method as with the Gnome control, and activating the xscreensaver deamon, you can edit the settings in a GUI.  Save on newbies and terminal flub ups!

---

