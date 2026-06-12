---
title: "C++ code, CodeLite and SDL library"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by machdohvah on 2011-04-28
```
// DECKSHOW.CPP

// 27Apr2011 modified for Ubuntu with SDL libraries

#include "SDL/SDL.h"
#include <stdlib.h>
#include <stdio.h>

#define PATH_TO_CARDS "/home/michael/cards/pxl/"

void MyLock();
void MyUnLock();
void PutPixelsFromFile(int,int);
void putpixel(SDL_Surface *surface, int x, int y, Uint32 pixel);

void ProgramConstructor();
void ProgramDestructor();

char FileName[12];
SDL_Surface *screen;
SDL_Event event;
int MaxW;
int MaxH;

int main() {

  ProgramConstructor();

  // Cards are 101 pixels long and 72 pixels wide

  MyLock();
  sprintf(FileName,"AS"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"2S"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"3S"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"4S"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"5S"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"6S"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"7S"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"8S"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"9S"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"TS"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"JS"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"QS"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"KS"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"AH"); PutPixelsFromFile(   2, 294 );
  sprintf(FileName,"2H"); PutPixelsFromFile( 103, 294 );
  sprintf(FileName,"3H"); PutPixelsFromFile( 204, 294 );
  sprintf(FileName,"4H"); PutPixelsFromFile( 305, 294 );
  sprintf(FileName,"5H"); PutPixelsFromFile(   2, 367 );
  sprintf(FileName,"6H"); PutPixelsFromFile( 103, 367 );
  sprintf(FileName,"7H"); PutPixelsFromFile( 204, 367 );
  sprintf(FileName,"8H"); PutPixelsFromFile( 305, 367 );
  sprintf(FileName,"9H"); PutPixelsFromFile(   2, 440 );
  sprintf(FileName,"TH"); PutPixelsFromFile( 103, 440 );
  sprintf(FileName,"JH"); PutPixelsFromFile( 204, 440 );
  sprintf(FileName,"QH"); PutPixelsFromFile( 305, 440 );
  sprintf(FileName,"KH"); PutPixelsFromFile(   2, 513 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"AC"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"2C"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"3C"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"4C"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"5C"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"6C"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"7C"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"8C"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"9C"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"TC"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"JC"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"QC"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"KC"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"AD"); PutPixelsFromFile(   2, 294 );
  sprintf(FileName,"2D"); PutPixelsFromFile( 103, 294 );
  sprintf(FileName,"3D"); PutPixelsFromFile( 204, 294 );
  sprintf(FileName,"4D"); PutPixelsFromFile( 305, 294 );
  sprintf(FileName,"5D"); PutPixelsFromFile(   2, 367 );
  sprintf(FileName,"6D"); PutPixelsFromFile( 103, 367 );
  sprintf(FileName,"7D"); PutPixelsFromFile( 204, 367 );
  sprintf(FileName,"8D"); PutPixelsFromFile( 305, 367 );
  sprintf(FileName,"9D"); PutPixelsFromFile(   2, 440 );
  sprintf(FileName,"TD"); PutPixelsFromFile( 103, 440 );
  sprintf(FileName,"JD"); PutPixelsFromFile( 204, 440 );
  sprintf(FileName,"QD"); PutPixelsFromFile( 305, 440 );
  sprintf(FileName,"KD"); PutPixelsFromFile(   2, 513 );
  MyUnLock();
  
  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"CB0"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"CB1"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"CB2"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"CB3"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"CB4"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"CB5"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"CB6"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"CB7"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"CB8"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"CB9"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"CBA"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"CBB"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"CBC"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"CBD"); PutPixelsFromFile( 103, 221 );
  sprintf(FileName,"CBE"); PutPixelsFromFile( 204, 221 );
  sprintf(FileName,"CBF"); PutPixelsFromFile( 305, 221 );

  sprintf(FileName,"BYC_0"); PutPixelsFromFile(   2, 294 );
  sprintf(FileName,"BYC_1"); PutPixelsFromFile( 103, 294 );
  sprintf(FileName,"BYC_2"); PutPixelsFromFile( 204, 294 );
  sprintf(FileName,"BYC_3"); PutPixelsFromFile( 305, 294 );
  sprintf(FileName,"BYC_4"); PutPixelsFromFile(   2, 367 );
  sprintf(FileName,"BYC_5"); PutPixelsFromFile( 103, 367 );
  sprintf(FileName,"BYC_6"); PutPixelsFromFile( 204, 367 );
  sprintf(FileName,"BYC_7"); PutPixelsFromFile( 305, 367 );
  sprintf(FileName,"BYC_8"); PutPixelsFromFile(   2, 440 );
  sprintf(FileName,"BYC_9"); PutPixelsFromFile( 103, 440 );
  sprintf(FileName,"BYC_A"); PutPixelsFromFile( 204, 440 );
  sprintf(FileName,"BYC_B"); PutPixelsFromFile( 305, 440 );
  sprintf(FileName,"BYC_C"); PutPixelsFromFile(   2, 513 );
  sprintf(FileName,"BYC_D"); PutPixelsFromFile( 103, 513 );
  sprintf(FileName,"BYC_E"); PutPixelsFromFile( 204, 513 );
  sprintf(FileName,"BYC_F"); PutPixelsFromFile( 305, 513 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"DIAG0"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"DIAG1"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"DIAG2"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"DIAG3"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"DIAG4"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"DIAG5"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"DIAG6"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"DIAG7"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"DIAG8"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"DIAG9"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"DIAGA"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"DIAGB"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"DIAGC"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"DIAGD"); PutPixelsFromFile( 103, 221 );
  sprintf(FileName,"DIAGE"); PutPixelsFromFile( 204, 221 );
  sprintf(FileName,"DIAGF"); PutPixelsFromFile( 305, 221 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"CARDHOLE"); PutPixelsFromFile(    2,   2 );
  sprintf(FileName,"Z2"); PutPixelsFromFile(        103,   2 );
  sprintf(FileName,"BLACKOUT"); PutPixelsFromFile(  204,   2 );
  sprintf(FileName,"ROYAL"); PutPixelsFromFile(     305,   2 );

  sprintf(FileName,"Z1"); PutPixelsFromFile(          2,  75 );
  sprintf(FileName,"DECKSIDE"); PutPixelsFromFile(  103,  75 );

  sprintf(FileName,"NORTHWRD"); PutPixelsFromFile(    2, 294 );
  sprintf(FileName,"SOUTHWRD"); PutPixelsFromFile(   32, 294 );
  sprintf(FileName,"EASTWORD"); PutPixelsFromFile(   62, 294 );
  sprintf(FileName,"WESTWORD"); PutPixelsFromFile(   92, 294 );
  sprintf(FileName,"SUIT"); PutPixelsFromFile(      122, 294 );
  sprintf(FileName,"WHONE"); PutPixelsFromFile(     152, 294 );
  sprintf(FileName,"WHTWO"); PutPixelsFromFile(     152, 324 );
  sprintf(FileName,"WHTHREE"); PutPixelsFromFile(   152, 354 );
  sprintf(FileName,"WHFOUR"); PutPixelsFromFile(    152, 384 );
  sprintf(FileName,"WHFIVE"); PutPixelsFromFile(    152, 414 );
  sprintf(FileName,"WHSIX"); PutPixelsFromFile(     152, 444 );
  sprintf(FileName,"BRONE"); PutPixelsFromFile(     182, 294 );
  sprintf(FileName,"BRTWO"); PutPixelsFromFile(     182, 324 );
  sprintf(FileName,"BRTHREE"); PutPixelsFromFile(   182, 354 );
  sprintf(FileName,"BRFOUR"); PutPixelsFromFile(    182, 384 );
  sprintf(FileName,"BRFIVE"); PutPixelsFromFile(    182, 414 );
  sprintf(FileName,"BRSIX"); PutPixelsFromFile(     182, 444 );
  sprintf(FileName,"WH_2"); PutPixelsFromFile(      212, 294 );
  sprintf(FileName,"WH_4"); PutPixelsFromFile(      212, 324 );
  sprintf(FileName,"WH_8"); PutPixelsFromFile(      212, 354 );
  sprintf(FileName,"WH16"); PutPixelsFromFile(      212, 384 );
  sprintf(FileName,"WH32"); PutPixelsFromFile(      212, 414 );
  sprintf(FileName,"WH64"); PutPixelsFromFile(      212, 444 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"DOT1"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"DOT2"); PutPixelsFromFile(   2,  35 );
  MyUnLock();

  SDL_Delay(1000);

  ProgramDestructor();

  return 0;
}

void MyLock() {
  if ( SDL_MUSTLOCK(screen) ) {
    if ( SDL_LockSurface(screen) < 0 ) {
      fprintf(stderr, "Can't lock screen: %s\n", SDL_GetError());
      exit(0);
    }
  }
}

void MyUnLock() {
  if ( SDL_MUSTLOCK(screen) ) {
    SDL_UnlockSurface(screen);
  }
  SDL_UpdateRect(screen, 0, 0, MaxW, MaxH);
}

void PutPixelsFromFile(int Yref, int Xref) {
  int x, y=0, Color;
  FILE *in;
  int Width;
  char StringBuffer[80];
  char sb[640];

sprintf(StringBuffer,"%s%s.PXL",PATH_TO_CARDS,FileName);
  if ( (in = fopen(StringBuffer, "rb")) != NULL ) {

  fgets(sb, 640, in );
  while ( !feof(in) ) {
    Width = SDL_strlen(sb);
    for (x=0; x<Width; x++) {
      Color = -1;
      switch (sb[x]) {
      case '0': Color =  0; break;
      case '1': Color =  1; break;
      case '2': Color =  2; break;
      case '3': Color =  3; break;
      case '4': Color =  4; break;
      case '5': Color =  5; break;
      case '6': Color =  6; break;
      case '7': Color =  7; break;
      case '8': Color =  8; break;
      case '9': Color =  9; break;
      case 'A': Color = 10; break;
      case 'B': Color = 11; break;
      case 'C': Color = 12; break;
      case 'D': Color = 13; break;
      case 'E': Color = 14; break;
      case 'F': Color = 15; break;
      }
      if (Color != -1) {
        putpixel( screen, x+Xref, y+Yref, Color );
      }
    }
    y++;
    fgets(sb, 640, in );
  }
  fclose( in );

  }
}

void putpixel(SDL_Surface *surface, int x, int y, Uint32 pixel) {
  int bpp = surface->format->BytesPerPixel;

  /* Here p is the address to the pixel we want to set */
  Uint8 *p = (Uint8 *)surface->pixels + y * surface->pitch + x * bpp;

  switch(bpp) {
  case 1:
    *p = pixel;
    break;
  case 2:
    *(Uint16 *)p = pixel;
     break;
  case 3:
    if(SDL_BYTEORDER == SDL_BIG_ENDIAN) {
      p[0] = (pixel >> 16) & 0xff;
      p[1] = (pixel >> 8) & 0xff;
      p[2] = pixel & 0xff;
    } else {
      p[0] = pixel & 0xff;
      p[1] = (pixel >> 8) & 0xff;
      p[2] = (pixel >> 16) & 0xff;
    }
    break;
  case 4:
    *(Uint32 *)p = pixel;
    break;
  }
}

void ProgramConstructor() {
  if( SDL_Init(SDL_INIT_EVERYTHING) < 0 ) {
    fprintf(stderr,
            "Couldn't initialize SDL: %s\n", SDL_GetError());
    exit(1);
  }

/* Clean up on exit */
  atexit(SDL_Quit);
    
/* Have a preference for 8-bit, but accept any depth */
  screen = SDL_SetVideoMode(1920, 1080, 16, SDL_SWSURFACE|SDL_ANYFORMAT);
  if ( screen == NULL ) {
    fprintf(stderr, "Couldn't set 1920x1080x16 video mode: %s\n", SDL_GetError());
    exit(1);
  }

  MaxW = screen->w;
  MaxH = screen->h;
}

void ProgramDestructor() {
  SDL_Quit();
}

```

My problem is that even though I have the appropriate libraries referenced, when I run the program... I get a blank window for the duration of the program and nothing else. I gave up on Geany for it had no debugger and moved on to CodeLite. My program is suppose to display my collection of pixel maps for each card in the playing card deck and other similar files in four screens, one right after the other. But, nothing happens. And, no error message. You will note the putpixel function that came right out of the SDL documentation. I got the function to work when running their example program that puts only one dot in yellow on the screen. But, then I tried to implement it in one of my actual programs and it failed.

Please help.

g++ in CodeLite 2.7.0.4375 with  SDL libraries.

---

### Post by mutinystudios on 2011-04-28
> **machdohvah said:**
> ```
// DECKSHOW.CPP

// 27Apr2011 modified for Ubuntu with SDL libraries

#include "SDL/SDL.h"
#include <stdlib.h>
#include <stdio.h>

#define PATH_TO_CARDS "/home/michael/cards/pxl/"

void MyLock();
void MyUnLock();
void PutPixelsFromFile(int,int);
void putpixel(SDL_Surface *surface, int x, int y, Uint32 pixel);

void ProgramConstructor();
void ProgramDestructor();

char FileName[12];
SDL_Surface *screen;
SDL_Event event;
int MaxW;
int MaxH;

int main() {

  ProgramConstructor();

  // Cards are 101 pixels long and 72 pixels wide

  MyLock();
  sprintf(FileName,"AS"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"2S"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"3S"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"4S"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"5S"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"6S"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"7S"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"8S"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"9S"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"TS"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"JS"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"QS"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"KS"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"AH"); PutPixelsFromFile(   2, 294 );
  sprintf(FileName,"2H"); PutPixelsFromFile( 103, 294 );
  sprintf(FileName,"3H"); PutPixelsFromFile( 204, 294 );
  sprintf(FileName,"4H"); PutPixelsFromFile( 305, 294 );
  sprintf(FileName,"5H"); PutPixelsFromFile(   2, 367 );
  sprintf(FileName,"6H"); PutPixelsFromFile( 103, 367 );
  sprintf(FileName,"7H"); PutPixelsFromFile( 204, 367 );
  sprintf(FileName,"8H"); PutPixelsFromFile( 305, 367 );
  sprintf(FileName,"9H"); PutPixelsFromFile(   2, 440 );
  sprintf(FileName,"TH"); PutPixelsFromFile( 103, 440 );
  sprintf(FileName,"JH"); PutPixelsFromFile( 204, 440 );
  sprintf(FileName,"QH"); PutPixelsFromFile( 305, 440 );
  sprintf(FileName,"KH"); PutPixelsFromFile(   2, 513 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"AC"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"2C"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"3C"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"4C"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"5C"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"6C"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"7C"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"8C"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"9C"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"TC"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"JC"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"QC"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"KC"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"AD"); PutPixelsFromFile(   2, 294 );
  sprintf(FileName,"2D"); PutPixelsFromFile( 103, 294 );
  sprintf(FileName,"3D"); PutPixelsFromFile( 204, 294 );
  sprintf(FileName,"4D"); PutPixelsFromFile( 305, 294 );
  sprintf(FileName,"5D"); PutPixelsFromFile(   2, 367 );
  sprintf(FileName,"6D"); PutPixelsFromFile( 103, 367 );
  sprintf(FileName,"7D"); PutPixelsFromFile( 204, 367 );
  sprintf(FileName,"8D"); PutPixelsFromFile( 305, 367 );
  sprintf(FileName,"9D"); PutPixelsFromFile(   2, 440 );
  sprintf(FileName,"TD"); PutPixelsFromFile( 103, 440 );
  sprintf(FileName,"JD"); PutPixelsFromFile( 204, 440 );
  sprintf(FileName,"QD"); PutPixelsFromFile( 305, 440 );
  sprintf(FileName,"KD"); PutPixelsFromFile(   2, 513 );
  MyUnLock();
  
  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"CB0"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"CB1"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"CB2"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"CB3"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"CB4"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"CB5"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"CB6"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"CB7"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"CB8"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"CB9"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"CBA"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"CBB"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"CBC"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"CBD"); PutPixelsFromFile( 103, 221 );
  sprintf(FileName,"CBE"); PutPixelsFromFile( 204, 221 );
  sprintf(FileName,"CBF"); PutPixelsFromFile( 305, 221 );

  sprintf(FileName,"BYC_0"); PutPixelsFromFile(   2, 294 );
  sprintf(FileName,"BYC_1"); PutPixelsFromFile( 103, 294 );
  sprintf(FileName,"BYC_2"); PutPixelsFromFile( 204, 294 );
  sprintf(FileName,"BYC_3"); PutPixelsFromFile( 305, 294 );
  sprintf(FileName,"BYC_4"); PutPixelsFromFile(   2, 367 );
  sprintf(FileName,"BYC_5"); PutPixelsFromFile( 103, 367 );
  sprintf(FileName,"BYC_6"); PutPixelsFromFile( 204, 367 );
  sprintf(FileName,"BYC_7"); PutPixelsFromFile( 305, 367 );
  sprintf(FileName,"BYC_8"); PutPixelsFromFile(   2, 440 );
  sprintf(FileName,"BYC_9"); PutPixelsFromFile( 103, 440 );
  sprintf(FileName,"BYC_A"); PutPixelsFromFile( 204, 440 );
  sprintf(FileName,"BYC_B"); PutPixelsFromFile( 305, 440 );
  sprintf(FileName,"BYC_C"); PutPixelsFromFile(   2, 513 );
  sprintf(FileName,"BYC_D"); PutPixelsFromFile( 103, 513 );
  sprintf(FileName,"BYC_E"); PutPixelsFromFile( 204, 513 );
  sprintf(FileName,"BYC_F"); PutPixelsFromFile( 305, 513 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"DIAG0"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"DIAG1"); PutPixelsFromFile( 103,   2 );
  sprintf(FileName,"DIAG2"); PutPixelsFromFile( 204,   2 );
  sprintf(FileName,"DIAG3"); PutPixelsFromFile( 305,   2 );
  sprintf(FileName,"DIAG4"); PutPixelsFromFile(   2,  75 );
  sprintf(FileName,"DIAG5"); PutPixelsFromFile( 103,  75 );
  sprintf(FileName,"DIAG6"); PutPixelsFromFile( 204,  75 );
  sprintf(FileName,"DIAG7"); PutPixelsFromFile( 305,  75 );
  sprintf(FileName,"DIAG8"); PutPixelsFromFile(   2, 148 );
  sprintf(FileName,"DIAG9"); PutPixelsFromFile( 103, 148 );
  sprintf(FileName,"DIAGA"); PutPixelsFromFile( 204, 148 );
  sprintf(FileName,"DIAGB"); PutPixelsFromFile( 305, 148 );
  sprintf(FileName,"DIAGC"); PutPixelsFromFile(   2, 221 );
  sprintf(FileName,"DIAGD"); PutPixelsFromFile( 103, 221 );
  sprintf(FileName,"DIAGE"); PutPixelsFromFile( 204, 221 );
  sprintf(FileName,"DIAGF"); PutPixelsFromFile( 305, 221 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"CARDHOLE"); PutPixelsFromFile(    2,   2 );
  sprintf(FileName,"Z2"); PutPixelsFromFile(        103,   2 );
  sprintf(FileName,"BLACKOUT"); PutPixelsFromFile(  204,   2 );
  sprintf(FileName,"ROYAL"); PutPixelsFromFile(     305,   2 );

  sprintf(FileName,"Z1"); PutPixelsFromFile(          2,  75 );
  sprintf(FileName,"DECKSIDE"); PutPixelsFromFile(  103,  75 );

  sprintf(FileName,"NORTHWRD"); PutPixelsFromFile(    2, 294 );
  sprintf(FileName,"SOUTHWRD"); PutPixelsFromFile(   32, 294 );
  sprintf(FileName,"EASTWORD"); PutPixelsFromFile(   62, 294 );
  sprintf(FileName,"WESTWORD"); PutPixelsFromFile(   92, 294 );
  sprintf(FileName,"SUIT"); PutPixelsFromFile(      122, 294 );
  sprintf(FileName,"WHONE"); PutPixelsFromFile(     152, 294 );
  sprintf(FileName,"WHTWO"); PutPixelsFromFile(     152, 324 );
  sprintf(FileName,"WHTHREE"); PutPixelsFromFile(   152, 354 );
  sprintf(FileName,"WHFOUR"); PutPixelsFromFile(    152, 384 );
  sprintf(FileName,"WHFIVE"); PutPixelsFromFile(    152, 414 );
  sprintf(FileName,"WHSIX"); PutPixelsFromFile(     152, 444 );
  sprintf(FileName,"BRONE"); PutPixelsFromFile(     182, 294 );
  sprintf(FileName,"BRTWO"); PutPixelsFromFile(     182, 324 );
  sprintf(FileName,"BRTHREE"); PutPixelsFromFile(   182, 354 );
  sprintf(FileName,"BRFOUR"); PutPixelsFromFile(    182, 384 );
  sprintf(FileName,"BRFIVE"); PutPixelsFromFile(    182, 414 );
  sprintf(FileName,"BRSIX"); PutPixelsFromFile(     182, 444 );
  sprintf(FileName,"WH_2"); PutPixelsFromFile(      212, 294 );
  sprintf(FileName,"WH_4"); PutPixelsFromFile(      212, 324 );
  sprintf(FileName,"WH_8"); PutPixelsFromFile(      212, 354 );
  sprintf(FileName,"WH16"); PutPixelsFromFile(      212, 384 );
  sprintf(FileName,"WH32"); PutPixelsFromFile(      212, 414 );
  sprintf(FileName,"WH64"); PutPixelsFromFile(      212, 444 );
  MyUnLock();

  SDL_Delay(1000);

  MyLock();
  sprintf(FileName,"DOT1"); PutPixelsFromFile(   2,   2 );
  sprintf(FileName,"DOT2"); PutPixelsFromFile(   2,  35 );
  MyUnLock();

  SDL_Delay(1000);

  ProgramDestructor();

  return 0;
}

void MyLock() {
  if ( SDL_MUSTLOCK(screen) ) {
    if ( SDL_LockSurface(screen) < 0 ) {
      fprintf(stderr, "Can't lock screen: %s\n", SDL_GetError());
      exit(0);
    }
  }
}

void MyUnLock() {
  if ( SDL_MUSTLOCK(screen) ) {
    SDL_UnlockSurface(screen);
  }
  SDL_UpdateRect(screen, 0, 0, MaxW, MaxH);
}

void PutPixelsFromFile(int Yref, int Xref) {
  int x, y=0, Color;
  FILE *in;
  int Width;
  char StringBuffer[80];
  char sb[640];

sprintf(StringBuffer,"%s%s.PXL",PATH_TO_CARDS,FileName);
  if ( (in = fopen(StringBuffer, "rb")) != NULL ) {

  fgets(sb, 640, in );
  while ( !feof(in) ) {
    Width = SDL_strlen(sb);
    for (x=0; x<Width; x++) {
      Color = -1;
      switch (sb[x]) {
      case '0': Color =  0; break;
      case '1': Color =  1; break;
      case '2': Color =  2; break;
      case '3': Color =  3; break;
      case '4': Color =  4; break;
      case '5': Color =  5; break;
      case '6': Color =  6; break;
      case '7': Color =  7; break;
      case '8': Color =  8; break;
      case '9': Color =  9; break;
      case 'A': Color = 10; break;
      case 'B': Color = 11; break;
      case 'C': Color = 12; break;
      case 'D': Color = 13; break;
      case 'E': Color = 14; break;
      case 'F': Color = 15; break;
      }
      if (Color != -1) {
        putpixel( screen, x+Xref, y+Yref, Color );
      }
    }
    y++;
    fgets(sb, 640, in );
  }
  fclose( in );

  }
}

void putpixel(SDL_Surface *surface, int x, int y, Uint32 pixel) {
  int bpp = surface->format->BytesPerPixel;

  /* Here p is the address to the pixel we want to set */
  Uint8 *p = (Uint8 *)surface->pixels + y * surface->pitch + x * bpp;

  switch(bpp) {
  case 1:
    *p = pixel;
    break;
  case 2:
    *(Uint16 *)p = pixel;
     break;
  case 3:
    if(SDL_BYTEORDER == SDL_BIG_ENDIAN) {
      p[0] = (pixel >> 16) & 0xff;
      p[1] = (pixel >> 8) & 0xff;
      p[2] = pixel & 0xff;
    } else {
      p[0] = pixel & 0xff;
      p[1] = (pixel >> 8) & 0xff;
      p[2] = (pixel >> 16) & 0xff;
    }
    break;
  case 4:
    *(Uint32 *)p = pixel;
    break;
  }
}

void ProgramConstructor() {
  if( SDL_Init(SDL_INIT_EVERYTHING) < 0 ) {
    fprintf(stderr,
            "Couldn't initialize SDL: %s\n", SDL_GetError());
    exit(1);
  }

/* Clean up on exit */
  atexit(SDL_Quit);
    
/* Have a preference for 8-bit, but accept any depth */
  screen = SDL_SetVideoMode(1920, 1080, 16, SDL_SWSURFACE|SDL_ANYFORMAT);
  if ( screen == NULL ) {
    fprintf(stderr, "Couldn't set 1920x1080x16 video mode: %s\n", SDL_GetError());
    exit(1);
  }

  MaxW = screen->w;
  MaxH = screen->h;
}

void ProgramDestructor() {
  SDL_Quit();
}

```

My problem is that even though I have the appropriate libraries referenced, when I run the program... I get a blank window for the duration of the program and nothing else. I gave up on Geany for it had no debugger and moved on to CodeLite. My program is suppose to display my collection of pixel maps for each card in the playing card deck and other similar files in four screens, one right after the other. But, nothing happens. And, no error message. You will note the putpixel function that came right out of the SDL documentation. I got the function to work when running their example program that puts only one dot in yellow on the screen. But, then I tried to implement it in one of my actual programs and it failed.

Please help.

g++ in CodeLite 2.7.0.4375 with  SDL libraries.

well it looks like you came accrose a bug which right now means that you script is all nice and clean but you didn't code it right. Sorry though you just need to go through it a couple more times. Sorry i couldn't really help though, i only code VB.:(

---

### Post by machdohvah on 2011-04-28
> **mutinystudios said:**
> well it looks like you came accrose a bug which right now means that you script is all nice and clean but you didn't code it right. Sorry though you just need to go through it a couple more times. Sorry i couldn't really help though, i only code VB.:(

Look. I have been programming on computer for longer then you have been living. It is obvious you do not know anything about C++, so you do not have to respond to this for you are not of any help.

---

