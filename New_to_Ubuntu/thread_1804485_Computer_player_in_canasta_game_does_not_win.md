---
title: "Computer player in canasta game does not win"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by machdohvah on 2011-07-14
I have created a computer game of canasta using dosbox, Borland Turbo C++, and Borland's graphics. The problem is that the computer player does not seem to ever win. I would like help in solving this problem. Thank you to all the participants in this thread in advance. :)

```


#define PROGNAME "GCANASTA"
#define VERSION "15Jul2011"
#define AUTHOR "Michael Flower"

/*

New program (rendered here) ...

GCANASTA.CPP graphic version with entire re-write.

24Nov2007 This started life as a character based system with mouse
attached. That program had too many bugs in it.

26Jan2008 Finished a working game with computer player logic.

29Aug2009 Corrected ComputerTurn to check EndRound at beginning.

30Aug2009 Corrected errors in ComputerTurn.

31Aug2009 There are several problems. Something in ComputerTurn is now
producing an endless loop and I counted ten sevens during play. Nasty!
Decided to remove the DOS SORT calls and replace them with qsort. The
computer locks up when player takes successfully on the first move.

01Sep2009 Tried to OVERLAY this thing but have yet to produce an OVR file.
The computer hand is corrupted upon melding. It appearently is erasing the
wrong cards after it melds the correct ones. Bug corrected: incorrect index
reference.

06Sep2009 Removed all penalties in figuring the score.

12Sep2009 Moved the Meld menu to left edge. Added Save and Restore.

31Oct2010 Reprogrammed the menus.

07Nov2010 Removed conditional on cOutCapabile.

08Nov2010 Changed condition from <= 2 to < 1. gpMeldedBefore and
gcMeldedBefore cancelled between rounds.

14Jul2011 Removed all "far" references as I started to compile this
again in "dosbox" in root terminal with Ubuntu 10.10 operating system.
Introduced NUMBER_CANASTA_OUT, NUMBER_CARDS_DRAW, gpHandCardCount,
and gcHandCardCount. Corrected problem of one card in hand left with
respect to NUMBER_CANASTA_OUT during discard. Created pCalcFirstMeld
on Status Line.

15Jul2011 Returned "far" references to data and functions for it was
over-running its memory.


  NOTE: All rules of Canasta in Hoyle are followed. This is the Two-Hand
Canasta variation. "Hoyle's Rules of Games" by Albert H Morehead and
Geoffrey Mott-Smith, revised and updated by Philip D Morehead, Dec2001
edition, page 140.

The definition of TESTING is only needed while debugging the program.

*/

// #define TESTING

#include <conio.h>
#include <ctype.h>
#include <graphics.h>
#include <stdarg.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

/*

Compile with "MLFMOUSE.CPP". This program uses the mouse object
developed purely from interrupts in assembly code. "MouseInfo"
structure is included there.

*/

#include "mlfmouse.h"
struct MouseInfo gMouseInformation = { 0, 0, 0, 0, 0 };

#define DECK_SIZE 108
#define DESKTOP_BUTTON_COUNT 6
#define DISCARD_PULLDOWN_COUNT 15
#define EMPTY -1
#define GAME_PULLDOWN_COUNT 1
#define HELP_PULLDOWN_COUNT 1
#define MAX_ROUNDS 8
#define MELD_DEPTH 15
#define MELD_LOCATIONS 12
#define MELD_PULLDOWN_COUNT 15
#define NATURAL_RANK_PULLDOWN_COUNT 11
#define NUMBER_CANASTA_OUT 2
#define NUMBER_CARDS_DRAW 2
#define STATUS_FOR 14
#define STATUS_BACK 6
#define STATUS_LINE 59
#define STOCK_COLUMN 30
#define STOCK_ROW 24

/*

Eventually, these two will be the current directory.

*/

#define PATH_TO_BGI "\\TC\\BGI"
// #define PATH_TO_BGI ""
#define PATH_TO_CARDS "\\MYDOCS\\TC\\CARDS\\PXL\\"
// #define PATH_TO_CARDS ""

enum {COMPUTER, PLAYER, NUM_PLAYERS};
enum bool {false, true};

/*

Cards are shuffled in this program by sorting on random numbers. The
Title field is only two characters long. Rank and Suit are needed for
sorting the hands. Rank is a number that is in line with its rank in
the game while Title contains the name of the card. This seperation is
needed for the jokers. All arrays with +1 allocation are there for
avoiding sort aliocation errors.

*/

class cCard {
public:
  char Shuffle[4], Title[3], Rank, Suit;
  int Value;
  bool IsWild;
};

cCard far gCard[DECK_SIZE+1];

/*

New cards in the hand are placed at the end of the hand and later
sorted. The hand only holds the rank and the card index
for all the other information is static with the card itself.

*/

class cHand {
public:
  char Rank; // for sorting
  int Index;
  bool Selected;
};

cHand far gHand[NUM_PLAYERS+1][DECK_SIZE+1];

/*

All threes are in Meld0. Meld1 thru MELD_LOCATIONS is in order of
rank string minus the wild cards.

*/

class cMeld {
public:
  bool IsBook;
  bool HasWild;
  int Position[MELD_DEPTH+1];
};

cMeld far gMeld[NUM_PLAYERS+1][MELD_LOCATIONS+1];

/*

The desktop menu has two incarnations, one for each phase.

*/

class cMenu {
public:
  char letter;
  char *caption;
  int row1, col1, row2, col2;
};

cMenu far gDesktop[2][DESKTOP_BUTTON_COUNT+1] = {
  {
    {'t', " Take ",    0, 0, 0, 5},
    {'d', " Draw ",    0, 6, 0,11},
    {'s', " Save ",    0,12, 0,17},
    {'r', " Restore ", 0,18, 0,26},
    {'e', " Exit   ",  0,27, 0,34},
    {'h', " Help ",    0,74, 0,79}
  }, {
    {'m', " Meld ",    0, 0, 0, 5},
    {'d', " Discard ", 0, 6, 0,14},
    {'d', "      ",    0,15, 0,20},
    {'d', "         ", 0,21, 0,29},
    {'e', " Exit   ",  0,30, 0,37},
    {'h', " Help ",    0,74, 0,79}
  }
};

/*

The second choices are the only things in the pull-down.

*/

cMenu far gDiscardMenu[DISCARD_PULLDOWN_COUNT+1] = {
  {'3'," 3 Three ", 2, 6, 2,14},
  {'4'," 4 Four  ", 3, 6, 3,14},
  {'5'," 5 Five  ", 4, 6, 4,14},
  {'6'," 6 Six   ", 5, 6, 5,14},
  {'7'," 7 Seven ", 6, 6, 6,14},
  {'8'," 8 Eight ", 7, 6, 7,14},
  {'9'," 9 Nine  ", 8, 6, 8,14},
  {'t'," T Ten   ", 9, 6, 9,14},
  {'j'," J Jack  ",10, 6,10,14},
  {'q'," Q Queen ",11, 6,11,14},
  {'k'," K King  ",12, 6,12,14},
  {'a'," A Ace   ",13, 6,13,14},
  {'2'," 2 Two   ",14, 6,14,14},
  {'z'," Z Joker ",15, 6,15,14},
  {'x'," X DONE  ",16, 6,16,14}
};

cMenu far gMeldMenu[MELD_PULLDOWN_COUNT+1] = {
  {'3'," 3 Three ", 2, 1, 2, 9},
  {'4'," 4 Four  ", 3, 1, 3, 9},
  {'5'," 5 Five  ", 4, 1, 4, 9},
  {'6'," 6 Six   ", 5, 1, 5, 9},
  {'7'," 7 Seven ", 6, 1, 6, 9},
  {'8'," 8 Eight ", 7, 1, 7, 9},
  {'9'," 9 Nine  ", 8, 1, 8, 9},
  {'t'," T Ten   ", 9, 1, 9, 9},
  {'j'," J Jack  ",10, 1,10, 9},
  {'q'," Q Queen ",11, 1,11, 9},
  {'k'," K King  ",12, 1,12, 9},
  {'a'," A Ace   ",13, 1,13, 9},
  {'2'," 2 Two   ",14, 1,14, 9},
  {'z'," Z Joker ",15, 1,15, 9},
  {'x'," X DONE  ",16, 1,16, 9}
};

cMenu far gNatualRankMenu[NATURAL_RANK_PULLDOWN_COUNT+1] = {
  {'4'," 4 Four  ", 3, 6, 3,14},
  {'5'," 5 Five  ", 4, 6, 4,14},
  {'6'," 6 Six   ", 5, 6, 5,14},
  {'7'," 7 Seven ", 6, 6, 6,14},
  {'8'," 8 Eight ", 7, 6, 7,14},
  {'9'," 9 Nine  ", 8, 6, 8,14},
  {'t'," T Ten   ", 9, 6, 9,14},
  {'j'," J Jack  ",10, 6,10,14},
  {'q'," Q Queen ",11, 6,11,14},
  {'k'," K King  ",12, 6,12,14},
  {'a'," A Ace   ",13, 6,13,14}
};

cMenu far gHelpMenu[HELP_PULLDOWN_COUNT+1] = {
  {'a'," About GCANASTA ", 2,63, 2,78}
};

/*

Miscellanious globals

*/

int    gBonusPoints[MAX_ROUNDS+1][NUM_PLAYERS+1];
char * gCardBackFileName = "FILENAME.EXT";
bool   gChanged = true;
int    gDiscard[DECK_SIZE+1];
bool   gEndGame = false;
bool   gEndRound = false;
int    gLastCB = 0;
int    gMeldPoints[MAX_ROUNDS+1][NUM_PLAYERS+1];
int    gNextCardInStock = EMPTY;
int    gPhase = 0;
char * gRankString = "3456789TJQKA2Z";
int    gRounds = 1;
int    gScore[MAX_ROUNDS+1][NUM_PLAYERS+1];
int    gStock[DECK_SIZE+1];
char * gSuitString = "HDSC";
int    gTextHeight;
int    gTextWidth;
int    gTopPile;

int    gcCanastaCount = 0;
int    gpCanastaCount = 0;
int    gcHandCardCount = 0;
int    gpHandCardCount = 0;
bool   gcMeldedBefore = false;
bool   gpMeldedBefore = false;
bool   gBlack3PreviousTurn = false;
int    gNextAvailableMeldPit = 0;
int    gWildsOnTable = 0;
int    gKnatsOnTable = 0;
bool   gWildInDiscardPile = false;

char   s[80] = "";
char   record[DECK_SIZE][80];

/*

Function declarations (c- = computer; p- = player)

*/

void far Abort(int l, char *s);
void far About();
int  far pCalcFirstMeld();
void far ComputerTurn();
void far DeselectAllInHand(int who);
void far cDiscard( int Which, int Where );
bool far pDiscard();
void far DisplayCard( int Card, int Row, int Col, bool Sideways );
bool far cDraw();
bool far pDraw();
int  far DrawCard(int who);
void far FigureScore(int r);
int  far cFindBlackThree();
int  far cFindMeldPit( char NaturalToMeld);
int  far cFindNaturalLowCountRank();
int  far cFindWild();
bool far cFirstMeld();
void far GetPixelsFromFile(char *filename, int Row, int Col,
       bool Sideways);
void far Gprintf( int Row, int Col, int ForColor, int BackColor,
       char *FormatString, ... );
void far HideMenu(cMenu* PullDown, int Entries);
bool far IsRedThree(int who, int N);
char far pMeld(bool ForTake);
void far cMeldAllNaturals();
int  far cMinLegalMeld();
bool far pMinLegalMeld(bool ForTake);
void far NextCardBack();
void far cOutCapabile();
char far ReadDesktop();
char far ReadMenu(cMenu *PullDown, int Entries);
void far Refresh();
void far RestoreBehindWindow(char *FileName, int Top, int Left,
       int Bottom, int Right);
void far RestoreStateOfComputer();
void far SaveBehindWindow(char *FileName, int Top, int Left,
       int Bottom, int Right);
void far SaveStateOfComputer();
int  far SelectCardInHand(int who, char a);
void far ShowMelds(int Who, int Row);
void far ShowMenu(cMenu *PullDown, int Entries);
void far ShowScore();
void far ShuffleDeck();
void far SortHand(int who);
void far StartOver();
bool far pTake();
bool far cTryTakeDiscard();
void far WaitASec();
int  far cWhereInHand( int Object );

void far ProgramConstructor();
bool far MainLoop();
void far ProgramDestructor();
void far pd2();

int  far sort_function( const void *a, const void *b);

/*

Program entry point. Calls the constructor, maintains the main loop,
and then calls the destructor.

*/

void main() {
  ProgramConstructor();
  while (MainLoop());
  ProgramDestructor();
}

/*

This function alerts the user what line called the function and for
what reason, calls the destructor, then aborts the program.

*/

void far Abort(int l, char *s) {
  cleardevice();
  Gprintf(1,1,YELLOW,BLACK,"%s aborted on line %d for this reason:",
    PROGNAME,l);
  Gprintf(2,1,YELLOW,BLACK,"%s",s);
  Gprintf(3,1,YELLOW,BLACK,"Press a key to continue...");
  getch();
  ProgramDestructor();
}

/*

This function shows a window that shows an announcement of information
about the program.

*/

void far About() {
  int I=0;

  SaveBehindWindow("ABTSAVE.DTA",25,26,38,54);
  Gprintf(25,26, BLACK, WHITE, "ÚÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ¿");
  Gprintf(26,26, BLACK, WHITE, "³ %s                 ³%c",PROGNAME,
    0xB2);
  Gprintf(27,26, BLACK, WHITE, "³ %s                ³%c", VERSION,
    0xB2);
  Gprintf(28,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2);
  Gprintf(29,26, BLACK, WHITE, "³ This program was written ³%c",0xB2);
  Gprintf(30,26, BLACK, WHITE, "³ by %s        ³%c",AUTHOR,0xB2);
  Gprintf(31,26, BLACK, WHITE, "³ and is intended as a     ³%c",0xB2);
  Gprintf(32,26, BLACK, WHITE, "³ demonstraion only and is ³%c",0xB2);
  Gprintf(33,26, BLACK, WHITE, "³ not for sale or lease to ³%c",0xB2);
  Gprintf(34,26, BLACK, WHITE, "³ anyone.                  ³%c",0xB2);
  Gprintf(35,26, BLACK, WHITE, "ÃÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄŽ%c",0xB2);
  Gprintf(36,26, BLACK, WHITE, "³ For the rules, see Hoyle ³%c",0xB2);
  Gprintf(37,26, BLACK, WHITE, "ÀÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ%c",0xB2);
  for (I=27;I<=54;I++) {
    Gprintf(38, I, BLACK, WHITE, "%c",0xB2);
  }
  ReadDesktop();
  RestoreBehindWindow("ABTSAVE.DTA",25,26,38,54);
}

/*

This function simulates the opponent player. It looks for a black
three, remembers if there was a black three in the previous turn and if
the discard pile has been taken in this turn. Depending on the result,
it tries to take the discard pile. Failing to take the discard pile, he
draws two cards. Depending on if he was finished with the previous
black three, he melds all the naturals he can. He checks to see if he
is capable to "go out". He checks for a first meld. He looks for a
black three, a wild, or a natural to discard ending his turn.

*/

void far ComputerTurn() {
  int BlackThree = EMPTY;
  bool ComputerTake = false;
  int Wild = EMPTY;
  int DeckIndex = 0;

  if (gEndRound) return;
  Refresh();
  BlackThree = cFindBlackThree();
  if (!gBlack3PreviousTurn) {
    if (cTryTakeDiscard()) {
      ComputerTake = true;
    }
  }
  if (!ComputerTake) {
    if (cDraw()) {
      gBlack3PreviousTurn = false;
    }
  }
  if ( !gcMeldedBefore ) gcMeldedBefore = cFirstMeld();
  if (gcMeldedBefore) cMeldAllNaturals();
// 07Nov2010 Removed conditional on cOutCapabile.
  cOutCapabile();
  Wild = cFindWild();
  if ( BlackThree != EMPTY ) {
    DeckIndex = BlackThree;
    cDiscard( DeckIndex, cWhereInHand( DeckIndex ));
    gBlack3PreviousTurn = true;
  }
  else {
    if ( !(gBlack3PreviousTurn) && !(gWildInDiscardPile) && (Wild != EMPTY) ) {
      DeckIndex = Wild;
      cDiscard( DeckIndex, cWhereInHand( DeckIndex ));
      gWildInDiscardPile = true;
    }
    else {
      DeckIndex = cFindNaturalLowCountRank();
      cDiscard( DeckIndex, cWhereInHand( DeckIndex ));
    }
  }
  gPhase = 0;
}

/*

This function de-selects all the cards in the specified hand.

*/

void far DeselectAllInHand(int who) {
  int I=0;

  for (;I<DECK_SIZE;I++)
    gHand[who][I].Selected = false;
}

/*

This function discards specified card from specified location in
the computer hand.

*/

void far cDiscard( int Which, int Where ) {
  if ( gcHandCardCount == 1)
    if ( gcCanastaCount < NUMBER_CANASTA_OUT ) return;

  gTopPile++;
  gDiscard[gTopPile] = Which;
  gHand[COMPUTER][Where].Index = EMPTY;
  gHand[COMPUTER][Where].Rank = '~';
  gHand[COMPUTER][Where].Selected = false;
  gcHandCardCount--;
  SortHand(COMPUTER);
}

/*

This function checks for minimum/legal meld, waits on the user to
specify a card for discard from his hand, removes the card from the
hand, places the card in the discard pile, sorts the hand in order of
rank, and checks for an empty hand declairing the round over.

*/

bool far pDiscard() {
  char a = ' ';
  int c,h;

  c=h=0;
  if (!(pMinLegalMeld(false))) return false;
/*

14Jul2011 Special case: If there is only one card left, disallow if
there are less then the NUMBER_CANASTA_OUT.

*/
  if ( gpHandCardCount == 1)
    if ( gpCanastaCount < NUMBER_CANASTA_OUT ) return false;

  for (;;) {
    a = ReadMenu(gDiscardMenu,DISCARD_PULLDOWN_COUNT);
    if (a == 0x0D) return false;
    a = toupper(a);
    if (a == 'X') return false;
    c = SelectCardInHand(PLAYER,a);
    if (c != EMPTY) break;
  }
  h = gHand[PLAYER][c].Index;
  gHand[PLAYER][c].Index = EMPTY;
  gHand[PLAYER][c].Rank = '~';
  gHand[PLAYER][c].Selected = false;
  gpHandCardCount--;
  gTopPile++;
  gDiscard[gTopPile] = h;
  SortHand(PLAYER);
  if (gpHandCardCount <= 0) gEndRound = true;

  return true;
}

/*

This function displays the selected card at specified row and col. It
needs to know if it is sideways or not.

*/

void far DisplayCard( int Card, int Row, int Col, bool Sideways ) {
  sprintf( s, "%s.PXL", gCard[Card].Title );
  GetPixelsFromFile( s, Row, Col, Sideways );
}

/*

Computer draws NUMBER_CARDS_DRAW cards storing the index and rank. It
shows a card back for each card as it processes. It notifies the caller
if it failed to draw a card.

*/

bool far cDraw() {
  int c=0,i;

for (i=0;i<NUMBER_CARDS_DRAW;i++) {
  c = DrawCard(COMPUTER);
  if (c == EMPTY) return false;
  gHand[COMPUTER][DECK_SIZE-(1+i)].Index = c;
  gHand[COMPUTER][DECK_SIZE-(1+i)].Rank = gCard[c].Rank;
  gcHandCardCount++;
  GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN-4+(2*i),
    false );
}

  SortHand(COMPUTER);
  WaitASec();

  return true;
}

/*

User draws NUMBER_CARDS_DRAW cards storing the index and rank. It shows
a card face for each card as it processes. It notifies the caller if it
failed to draw a card.

*/

bool far pDraw() {
  int c=0, i;

for (i=0;i<NUMBER_CARDS_DRAW;i++) {
  c = DrawCard(PLAYER);
  if (c == EMPTY) return false;
  gHand[PLAYER][DECK_SIZE-(1+i)].Index = c;
  gHand[PLAYER][DECK_SIZE-(1+i)].Rank = gCard[c].Rank;
  gpHandCardCount++;
  DisplayCard(c,STOCK_ROW,STOCK_COLUMN-4+(2*i),false);
}

  SortHand(PLAYER);
  WaitASec();

  return true;
}

/*

This function draws a card into the specified hand. It checks for an
empty stock pile, draws a card from stock, checks for red threes (Meld0
is for threes, red and black) drawing a replacement card if needed.

*/

int far DrawCard(int who) {
  int N;
  bool Continuing = true;

  N=0;
  while (Continuing) {
    if (gNextCardInStock == EMPTY) return EMPTY;
    Continuing = false;
    N = gStock[gNextCardInStock];
    gStock[gNextCardInStock] = EMPTY;
    gNextCardInStock--;
    if (IsRedThree(who, N)) Continuing = true;
  }
  return N;
}

/*

This function figures the score at the end of the round. Awards bonus
points, awards meld points, subtracts sorted hand, storing the running
total.

*/

void far FigureScore(int r) {
  int p,L,d,c;

  p=L=d=c=0;
  for (p=0;p<NUM_PLAYERS;p++) {
    gBonusPoints[r][p] = 0;
    for (L=1;L<MELD_LOCATIONS;L++) {
      if (gMeld[p][L].IsBook) {
        if(gMeld[p][L].HasWild)
             gBonusPoints[r][p] += 300; // black canasta
        else gBonusPoints[r][p] += 500; // red canasta
      }
    }

    for (L=0,d=0;L<MELD_DEPTH;L++) { // count red threes
      c = gMeld[p][0].Position[L];
      if (c == EMPTY) {
        break;
      }
      if ((gCard[c].Title[1] == 'H') ||
          (gCard[c].Title[1] == 'D')) {
        d++;
      }
    }
    gBonusPoints[r][p] += (d*100); // red three award

    gMeldPoints[r][p] = 0; // figure meld points
    for (L=0;L<MELD_LOCATIONS;L++) {
      for (d=0;d<MELD_DEPTH;d++) {
        c = gMeld[p][L].Position[d];
        if (c == EMPTY) {
          break;
        }
        gMeldPoints[r][p] += gCard[c].Value;
      }
    }

    for (L=0;L<DECK_SIZE;L++) { // deduct for cards in hand
      c = gHand[p][L].Index;
      if (c == EMPTY) {
        if (L==0) { // award 100 for going out
          gBonusPoints[r][p] += 100;
        }
        break;
      }
      else {
        gMeldPoints[r][p] -= gCard[c].Value;
      }
    }

    gScore[r][p] = gBonusPoints[r][p] + gMeldPoints[r][p];
    if (r > 0) gScore[r][p] += gScore[r-1][p];
  }
  if (gScore[r][PLAYER]   >= 5000) gEndGame = true;
  if (gScore[r][COMPUTER] >= 5000) gEndGame = true;
  if (r >= MAX_ROUNDS-1)           gEndGame = true;
}

/*

This function looks for a black three in computer hand sorted in order
by rank. Returns EMPTY if failed.

*/

int far cFindBlackThree() {
  int i;
  int Result = EMPTY;
  int DeckIndex;
  char a,b;

  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    a = gCard[DeckIndex].Title[0];
    b = gCard[DeckIndex].Title[1];
    if ( a == '3' ) {
      if ((b == 'S') || (b == 'C')) {
        Result = DeckIndex;
        break;
      }
    }
  }

  return Result;
}

/*

This function find an the right meld pit for the computer hand for a
given natural to meld. Returns EMPTY if not found.

*/

int far cFindMeldPit( char NaturalToMeld) {
  int i, j;
  char RankOfCardInList;
  int Result = EMPTY;
  int DeckIndex;

  gNextAvailableMeldPit = 0;
  gWildsOnTable = 0;
  gKnatsOnTable = 0;
  for (i=1; i<MELD_LOCATIONS; i++) {
    for ( j=0; j<MELD_DEPTH; j++ ) {
      DeckIndex = gMeld[COMPUTER][i].Position[j];
      if ( DeckIndex == EMPTY ) break;
      RankOfCardInList = gCard[DeckIndex].Title[0];
      if (( RankOfCardInList != 'Z' ) && ( RankOfCardInList != '2' )) {
        if ( NaturalToMeld == RankOfCardInList ) {
          Result = i;
          break;
        }
        else break;
      }
    }
    if ( Result != EMPTY ) break;
    if (( j == 0 && DeckIndex == EMPTY )) break;
  }
  if ( Result == EMPTY ) gNextAvailableMeldPit = i;
  else {
    for ( j=0; j<MELD_DEPTH; j++ ) {
      DeckIndex = gMeld[COMPUTER][Result].Position[j];
      if ( DeckIndex == EMPTY ) break;
      switch ( gCard[DeckIndex].Title[0] ) {
      case 'Z':
      case '2':
        gWildsOnTable++;
        break;
      default:
        gKnatsOnTable++;
      }
    }
  }

  return Result;
}

/*

This function finds the lowest rank and the lowest count of a natural
to discard from the computer hand.

*/

int far cFindNaturalLowCountRank() {
  int Result;
  int i, j;
  char RankOfCardInHand, *ptr;
  int NatCount[11];
  int DeckIndex;

  for (i=0; i<11; i++) NatCount[i] = 0;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInHand = gCard[DeckIndex].Title[0];
    ptr = strchr( gRankString, RankOfCardInHand );
    switch ( RankOfCardInHand ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      NatCount[(int) (ptr-gRankString)-1]++;
    }
  }
  RankOfCardInHand = ' ';
  for ( i=1; i<=8; i++) {
    for ( j=0; j<11; j++ ) {
      if ( NatCount[j] == i ) {
        RankOfCardInHand = gRankString[j+1];
        break;
      }
    }
    if ( RankOfCardInHand != ' ' ) break;
  }
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( gCard[DeckIndex].Title[0] == RankOfCardInHand ) {
      Result = DeckIndex;
      break;
    }
  }

  return Result;
}

/*

This function looks for a wild in the computer hand.

*/

int far cFindWild() {
  char RankOfCardInList;
  int i;
  int Result = EMPTY;
  int DeckIndex;

  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    if (( RankOfCardInList == '2' ) ||
        ( RankOfCardInList == 'Z' )) {
      Result = DeckIndex;
      break;
    }
  }

  return Result;
}

/*

This function attempts to meld from the computer hand for the first
time.

*/

bool far cFirstMeld() {
  int CardList[20];
  int i, j, k;
  int NatCount[11];
  int NaturalList[8];
  int NatInList;
  bool Pass = false;
  char *ptr;
  char RankOfCardInList;
  int cfmScore;
  int WildList[12];
  int WldInHand = 0;
  int DeckIndex;
  int MeldPit = 0;
  int cfmMinMeld = cMinLegalMeld();

  for (i=0; i<20; i++) CardList[i] = EMPTY;
  for (i=0; i<11; i++) NatCount[i] = 0;
  for (i=0; i<8; i++) NaturalList[i] = EMPTY;
  for (i=0; i<12; i++) WildList[i] = EMPTY;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    ptr = strchr( gRankString, RankOfCardInList );
    switch ( RankOfCardInList ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      NatCount[(int) (ptr-gRankString)-1]++;
    }
  }
  RankOfCardInList = ' ';
  for ( i=8; i>=2; i--) {
    for ( j=10; j>=0; j-- ) {
      if ( NatCount[j] == i ) {
        RankOfCardInList = gRankString[j+1];
        cfmScore = 0;
        NatInList = 0;
        for ( k=0; k<DECK_SIZE; k++ ) {
          DeckIndex = gHand[COMPUTER][k].Index;
          if ( DeckIndex == EMPTY ) break;
          if ( gCard[DeckIndex].Title[0] == RankOfCardInList ) {
            CardList[NatInList] = DeckIndex;
            NaturalList[NatInList++] = DeckIndex;
            cfmScore += gCard[DeckIndex].Value;
            if ( cfmScore >= cfmMinMeld ) break;
          }
        }
        if ( cfmScore >= cfmMinMeld ) Pass = true;
        else {
          Pass = false;
          for ( k=0; k<DECK_SIZE; k++ ) {
            DeckIndex = gHand[COMPUTER][k].Index;
            if ( DeckIndex == EMPTY ) break;
            if ( gCard[DeckIndex].Title[0] == 'Z' ) {
              CardList[NatInList+WldInHand] = DeckIndex;
              WildList[WldInHand++] = DeckIndex;
              cfmScore += gCard[DeckIndex].Value;
              if ( cfmScore >= cfmMinMeld ) {
                Pass = true;
                break;
              }
            }
          }
          if ( !Pass ) {
            for ( k=0; k<DECK_SIZE; k++ ) {
              DeckIndex = gHand[COMPUTER][k].Index;
              if ( DeckIndex == EMPTY ) break;
              if ( gCard[DeckIndex].Title[0] == '2' ) {
                CardList[NatInList+WldInHand] = DeckIndex;
                WildList[WldInHand++] = DeckIndex;
                cfmScore += gCard[DeckIndex].Value;
                if ( cfmScore >= cfmMinMeld ) {
                  Pass = true;
                  break;
                }
              }
            }
          }
          if ( NatInList <= WldInHand ) Pass = false;
        }
        if ( Pass ) break;
        else {
          NatInList = 0; WldInHand = 0;
          for ( k=0; k<20; k++ ) CardList[k] = EMPTY;
          for ( k=0; k<8; k++ ) NaturalList[k] = EMPTY;
          for ( k=0; k<12; k++ ) WildList[k] = EMPTY;
        }
      }
    }
    if ( Pass ) break;
  }
  if ( Pass ) {
    switch (RankOfCardInList) {
    case '4': MeldPit =  1; break;
    case '5': MeldPit =  2; break;
    case '6': MeldPit =  3; break;
    case '7': MeldPit =  4; break;
    case '8': MeldPit =  5; break;
    case '9': MeldPit =  6; break;
    case 'T': MeldPit =  7; break;
    case 'J': MeldPit =  8; break;
    case 'Q': MeldPit =  9; break;
    case 'K': MeldPit = 10; break;
    case 'A': MeldPit = 11; break;
    }
    for ( j=0; j<WldInHand; j++ ) {
      DeckIndex = WildList[j];
      if ( DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][MeldPit].Position[j] = DeckIndex;
    }
    for ( k=0; k<NatInList; k++ ) {
      DeckIndex = NaturalList[k];
      if ( DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][MeldPit].Position[j+k] = DeckIndex;
    }
    for (i=0; i<20; i++) {
      DeckIndex = CardList[i];
      if ( DeckIndex == EMPTY ) break;
      for ( j=0; j<DECK_SIZE; j++ ) {
        DeckIndex = gHand[COMPUTER][j].Index;
        if ( DeckIndex == CardList[i] ) break;
      }
      gHand[COMPUTER][j].Index = EMPTY;
      gHand[COMPUTER][j].Rank = '~';
      gHand[COMPUTER][j].Selected = false;
      gcHandCardCount--;
    }
    SortHand(COMPUTER);
  }

  return Pass;
}

/*

This function looks for hex representation in an ascii file. CRLF is
interpreted as the end of line. Each hex digit represents the color
values of 0 through 15. Other values are skipped. The color is then
placed on the screen pixle by pixle. All of the files must be present
for this program to run.

*/

void far GetPixelsFromFile(char *filename, int Row, int Col,
    bool Sideways) {
  int Yref = Row*gTextHeight;
  int Xref = Col*gTextWidth;
  int x, y, Color;
  FILE *in;
  int Width;
  char S[640]="";

  x=y=Color=Width=0;
  sprintf(S,"%s%s",PATH_TO_CARDS,filename);
  if ( (in = fopen(S, "rb")) == NULL ) {
    sprintf(S,"File not found: %s%s",PATH_TO_CARDS,filename);
    Abort(__LINE__,S);
    exit( 1 );
  }
  else {

  fgets(S, 640, in );
  while ( !feof(in) ) {
    Width = strlen(S);
    for (x=0; x<Width; x++) {
      Color = EMPTY;
      switch (S[x]) {
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
      case 'F': Color = 15;
      }
      if (Sideways) {
        if (Color != EMPTY) putpixel( y+312,278-x, Color );
      }
      else {
        if (Color != EMPTY) putpixel( x+Xref, y+Yref, Color );
      }
    }
    y++;
    fgets(S, 640, in );
  }
  fclose( in );

  }
}

/*

This function is intended to be a graphic replacement for a combination
of gotoxy, textcolor, textbachground, and cprintf using va_list,
vsprintf, setcolor, and outtextxy.

*/

void far Gprintf( int Row, int Col, int ForColor, int BackColor,
    char *FormatString, ... ) {
  va_list ArgumentPointer;
  int i=0;

  va_start( ArgumentPointer, FormatString );
  vsprintf( s, FormatString, ArgumentPointer );
  char BackStr[2] = {0xDB,0x00};
  setcolor( BackColor );
  for (; i<strlen( s ); i++)
    outtextxy( (Col+i) * gTextHeight, Row * gTextWidth, BackStr );
  setcolor( ForColor );
  outtextxy( Col * gTextHeight, Row * gTextWidth, s );
  va_end( ArgumentPointer );
}

/*

This function is used to hide the menu after a selection is made.

*/

void far HideMenu(cMenu* PullDown, int Entries) {
  int MenuWidth = strlen(PullDown[0].caption);
  int Top = PullDown[0].row1-1;
  int Left = PullDown[0].col1-1;
  int Bottom = PullDown[Entries-1].row1+1;
  int Right = PullDown[Entries-1].col1+MenuWidth;

  RestoreBehindWindow("MENUBACK.DTA", Top, Left, Bottom+1, Right+1);
}

/*

Test for red three and move to Meld0

*/

bool far IsRedThree(int who, int N) {
  int D;
  bool Result = false;

  if (gCard[N].Title[0] == '3') {
    switch(gCard[N].Suit) {
    case 'H': case 'D': // Red three
      for (D=0;D<MELD_DEPTH;D++) {
        if (gMeld[who][0].Position[D] == EMPTY) {
          gMeld[who][0].Position[D] = N;
          break;
        }
      }
      Result = true;
      break;
    }
  }
  return Result;
}

/*

Player Meld: Builds a queue of cards from the user selections
displaying a dot for each selection as it goes. It seperates the wilds
from the naturals, allows for only one rank, checks for all wilds and
assigns rank from the user, reverses all selection if failed, includes
the top of the discard pile if for taking, moves cards from the user
hand to his meld pit and returns the rank or blank. Rules for
individual meld are that naturals and wilds add to three cards and that
there are equal or more naturals then wilds in the melded result.

*/

char far pMeld(bool ForTake) {
  int b,c,i,j,n,p,q,r,t,w;
  int Queue[MELD_DEPTH];
  char a,RankOfQueue;

  b=c=n=p=q=r=t=w=0;
  a=RankOfQueue=' ';
  for (;q<MELD_DEPTH;q++) Queue[q] = EMPTY;
  if (ForTake) n=1;
  for (q=0;q<MELD_DEPTH;q++) {
    a = ReadMenu(gMeldMenu,MELD_PULLDOWN_COUNT);
    if (a == 0x0D) break;
    if (a == 'x') break;
    a = toupper(a);
    b = SelectCardInHand(PLAYER,a);
    if (b == EMPTY) q--;
    else {
      for (i=1;i<=5;i++) {
        for (j=(22*(i-1));j<(22*i);j++) {
          if (j>=DECK_SIZE) break;
          if (gHand[PLAYER][j].Index != EMPTY) {
            if (gHand[PLAYER][j].Selected) {
              Gprintf( STATUS_LINE-(6-i), (((22*i)-j-1)*3)+15, YELLOW,
                BLACK, "%c",0xFE);
            }
          }
        }
      }
      c = gHand[PLAYER][b].Index;
      Queue[q] = c;
      if (gCard[c].IsWild) {
        w++;
      }
      else {
        n++;
        if (RankOfQueue == ' ') RankOfQueue = a;
        else {
          if (RankOfQueue != a) {
            DeselectAllInHand(PLAYER);
            return ' ';
          }
        }
      }
    }
  }
  if (RankOfQueue == ' ') {
    if (ForTake) return ' ';
    cleardevice();
    Gprintf(1,1,YELLOW,BLACK,
      "On which rank do you want those wilds to be placed?");
    a = ReadMenu(gNatualRankMenu,NATURAL_RANK_PULLDOWN_COUNT);
    RankOfQueue = toupper(a);
  }
  switch (RankOfQueue) {
  case '3': r= 0; break;
  case '4': r= 1; break;
  case '5': r= 2; break;
  case '6': r= 3; break;
  case '7': r= 4; break;
  case '8': r= 5; break;
  case '9': r= 6; break;
  case 'T': r= 7; break;
  case 'J': r= 8; break;
  case 'Q': r= 9; break;
  case 'K': r=10; break;
  case 'A': r=11; break;
  default:
    DeselectAllInHand(PLAYER);
    return ' ';
  }
  for(t=0;t<MELD_DEPTH;t++) {
    p = gMeld[PLAYER][r].Position[t];
    if (p == EMPTY) break;
    if (gCard[p].IsWild)
         w++;
    else n++;
  }
  if ((n+w)<3) {
    DeselectAllInHand(PLAYER);
    return ' ';
  }
  else {
    if (n<w) {
      DeselectAllInHand(PLAYER);
      return ' ';
    }
    else {
      if (ForTake) {
        gMeld[PLAYER][r].Position[t] = gDiscard[gTopPile];
        gDiscard[gTopPile] = EMPTY;
        gTopPile--; t++;
      }
      for (q=0;q<MELD_DEPTH;q++,t++) {
        if (Queue[q] == EMPTY) break;
        gMeld[PLAYER][r].Position[t] = Queue[q];
        for (b=0;b<DECK_SIZE;b++) {
          if (gHand[PLAYER][b].Index == Queue[q]) break;
        }
        gHand[PLAYER][b].Index = EMPTY;
        gHand[PLAYER][b].Rank = '~';
        gHand[PLAYER][b].Selected = false;
        gpHandCardCount--;
      }
      gpMeldedBefore = true;
      SortHand(PLAYER);
    }
  }
  DeselectAllInHand(PLAYER);

  return RankOfQueue;
}

/*

This function melds all the natural cards it can from the computer
hand.

*/

void far cMeldAllNaturals() {

  int  CardList[20];
  int  i, j, k;
  int  MeldPit;
  int  NatCount[11];
  char *ptr;
  char RankOfCardInList;
  int  DeckIndex;

  for (i=0; i<11; i++) NatCount[i]= 0;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    ptr = strchr( gRankString, RankOfCardInList );
    switch ( RankOfCardInList ) {
    case 'Z':
    case '2':
    case '3':
      break;
    default:
      NatCount[(int) (ptr-gRankString)-1]++;
    }
  }
  for (i=0; i<20; i++) CardList[i] = EMPTY;
  RankOfCardInList = ' ';
  for ( i=8; i>2; i--) {
    for ( j=10; j>=0; j-- ) {
      if ( NatCount[j] == i ) {
        RankOfCardInList = gRankString[j+1];
        NatCount[j] = 0;
        break;
      }
    }
    if ( RankOfCardInList != ' ' ) break;
  }
  if ( RankOfCardInList != ' ' ) {
    for (i=0, j=0; i<DECK_SIZE; i++) {
      DeckIndex = gHand[COMPUTER][i].Index;
      if ( DeckIndex == EMPTY ) break;
      if ( gCard[DeckIndex].Title[0] == RankOfCardInList )
        CardList[j++] = DeckIndex;
    }
    MeldPit = cFindMeldPit( RankOfCardInList );
    if ( MeldPit == EMPTY ) {
      switch (RankOfCardInList) {
      case '4': MeldPit =  1; break;
      case '5': MeldPit =  2; break;
      case '6': MeldPit =  3; break;
      case '7': MeldPit =  4; break;
      case '8': MeldPit =  5; break;
      case '9': MeldPit =  6; break;
      case 'T': MeldPit =  7; break;
      case 'J': MeldPit =  8; break;
      case 'Q': MeldPit =  9; break;
      case 'K': MeldPit = 10; break;
      case 'A': MeldPit = 11; break;
      }
    }
    for (i=0; i<MELD_DEPTH; i++) {
      DeckIndex = gMeld[COMPUTER][MeldPit].Position[i];
      if ( DeckIndex == EMPTY ) break;
    }
    for ( j=0; j<MELD_DEPTH; j++ ) {
      DeckIndex = CardList[j];
      if ( DeckIndex == EMPTY ) break;
      gMeld[COMPUTER][MeldPit].Position[i+j] = DeckIndex;
      for ( k=0; k<DECK_SIZE; k++ ) {
        DeckIndex = gHand[COMPUTER][k].Index;
        if ( DeckIndex == CardList[j] ) break;
      }
      gHand[COMPUTER][k].Index = EMPTY;
      gHand[COMPUTER][k].Rank = '~';
      gHand[COMPUTER][k].Selected = false;
      gcHandCardCount--;
    }
    SortHand(COMPUTER);
  }
}

/*

This function returns the value of the minimum legal first meld score
stepped at 15, 50, 90, and 120 for a score from the previous round of
less than 0, 1500, 3000, and greater than 3000 for the computer hand.

*/

int far cMinLegalMeld() {
  int minmeld = 0;

  if (gRounds <= 1) {
    minmeld = 50;
  }
  else {
    if (gScore[gRounds-2][COMPUTER] >= 3000) {
      minmeld = 120;
    }
    else {
      if (gScore[gRounds-2][COMPUTER] >= 1500) {
        minmeld = 90;
      }
      else {
        if (gScore[gRounds-2][COMPUTER] >= 0) {
          minmeld = 50;
        }
        else {
          minmeld = 15;
        }
      }
    }
  }
  return minmeld;
}

/*

This function returns the value of the minimum legal first meld score
stepped at 15, 50, 90, and 120 for a score from the previous round of
less than 0, 1500, 3000, and greater than 3000 for the use hand.
Includes the top of the discard pile if for take. Returns all cards
back to the hand except red threes on fail.

*/

int far pCalcFirstMeld() {
  int retval = 0;

  if (gRounds <= 1) retval = 50;
  else {
    if (gScore[gRounds-2][PLAYER] >= 3000) retval = 120;
    else {
      if (gScore[gRounds-2][PLAYER] >= 1500) retval = 90;
      else {
        if (gScore[gRounds-2][PLAYER] >= 0) retval = 50;
        else retval = 15;
      }
    }
  }

  return retval;
}

bool far pMinLegalMeld(bool ForTake) {
  int L,D,C,currmeld,minmeld;

  L=D=C=currmeld=minmeld=0;
  minmeld = pCalcFirstMeld();
  for (L=1;L<MELD_LOCATIONS;L++) {
    for (D=0;D<=MELD_DEPTH;D++) {
      C = gMeld[PLAYER][L].Position[D];
      if (C == EMPTY) break;
      currmeld += gCard[C].Value;
    }
  }
  if ((currmeld > 0 ) && (currmeld < minmeld)) {
    if (ForTake) return false;
    cleardevice();
    Gprintf(1,1,YELLOW,BLACK,
      "All melds are being return to your hand.");
    Gprintf(2,1,YELLOW,BLACK,"Press a key to continue.");
    getch();
    gpMeldedBefore = false;
    for (C=0;C<DECK_SIZE;C++) {
      if (gHand[PLAYER][C].Index == EMPTY) break;
    }
    for (L=1;L<MELD_LOCATIONS;L++) {
      gMeld[PLAYER][L].IsBook = false;
      gMeld[PLAYER][L].HasWild = false;
      for (D=0;D<=MELD_DEPTH;D++) {
        if (gMeld[PLAYER][L].Position[D] == EMPTY) break;
        gHand[PLAYER][C].Index = gMeld[PLAYER][L].Position[D];
        gHand[PLAYER][C].Rank = gCard[gHand[PLAYER][C].Index].Rank;
        gMeld[PLAYER][L].Position[D] = EMPTY;
        gpHandCardCount++;
        C++;
      }
    }
    SortHand(PLAYER);
    return false;
  }
  return true;
}

/*

This function provides a variety of cardbacks.

*/

void far NextCardBack() {
  int a = gLastCB;

  while (a == gLastCB) a = rand() % 32;
  gLastCB = a;
  switch (a) {
  case  0: strcpy(gCardBackFileName, "CB0.PXL");   break;
  case  1: strcpy(gCardBackFileName, "CB1.PXL");   break;
  case  2: strcpy(gCardBackFileName, "CB2.PXL");   break;
  case  3: strcpy(gCardBackFileName, "CB3.PXL");   break;
  case  4: strcpy(gCardBackFileName, "CB4.PXL");   break;
  case  5: strcpy(gCardBackFileName, "CB5.PXL");   break;
  case  6: strcpy(gCardBackFileName, "CB6.PXL");   break;
  case  7: strcpy(gCardBackFileName, "CB7.PXL");   break;
  case  8: strcpy(gCardBackFileName, "CB8.PXL");   break;
  case  9: strcpy(gCardBackFileName, "CB9.PXL");   break;
  case 10: strcpy(gCardBackFileName, "CBA.PXL");   break;
  case 11: strcpy(gCardBackFileName, "CBB.PXL");   break;
  case 12: strcpy(gCardBackFileName, "CBC.PXL");   break;
  case 13: strcpy(gCardBackFileName, "CBD.PXL");   break;
  case 14: strcpy(gCardBackFileName, "CBE.PXL");   break;
  case 15: strcpy(gCardBackFileName, "CBF.PXL");   break;
  case 16: strcpy(gCardBackFileName, "BYC_0.PXL"); break;
  case 17: strcpy(gCardBackFileName, "BYC_1.PXL"); break;
  case 18: strcpy(gCardBackFileName, "BYC_2.PXL"); break;
  case 19: strcpy(gCardBackFileName, "BYC_3.PXL"); break;
  case 20: strcpy(gCardBackFileName, "BYC_4.PXL"); break;
  case 21: strcpy(gCardBackFileName, "BYC_5.PXL"); break;
  case 22: strcpy(gCardBackFileName, "BYC_6.PXL"); break;
  case 23: strcpy(gCardBackFileName, "BYC_7.PXL"); break;
  case 24: strcpy(gCardBackFileName, "BYC_8.PXL"); break;
  case 25: strcpy(gCardBackFileName, "BYC_9.PXL"); break;
  case 26: strcpy(gCardBackFileName, "BYC_A.PXL"); break;
  case 27: strcpy(gCardBackFileName, "BYC_B.PXL"); break;
  case 28: strcpy(gCardBackFileName, "BYC_C.PXL"); break;
  case 29: strcpy(gCardBackFileName, "BYC_D.PXL"); break;
  case 30: strcpy(gCardBackFileName, "BYC_E.PXL"); break;
  case 31: strcpy(gCardBackFileName, "BYC_F.PXL"); break;
  }
}

/*

This function checks for capability of computer hand to "go out".

*/

void far cOutCapabile() {
  int  Pos1;
  int  Pos2;
  int  i, j, k;
  int  Singletons = 0;
  int  Doubletons = 0;
  int  NatCount[12];
  int  MeldPit;
  int  WldCount = 0;
  char *ptr;
  char cocRank, cocOldRank;
  bool Pass = true;

// 14Jul2011 Changed condition from < 1 to < NUMBER_CANASTA_OUT
  if ( gcCanastaCount < NUMBER_CANASTA_OUT ) return;
  for (i=0; i<12; i++) NatCount[i]= 0;
  for (i=0; i<DECK_SIZE; i++) {
    Pos1 = gHand[COMPUTER][i].Index;
    if ( Pos1 == EMPTY ) break;
    cocRank = gCard[Pos1].Title[0];
    ptr = strchr( gRankString, cocRank );
    switch ( cocRank ) {
    case '2':
    case 'Z':
      WldCount++;
      break;
    default:
      NatCount[(int) (ptr-gRankString)]++;
    }
  }
  for (i=0; i<12; i++) {
    switch ( NatCount[i] ) {
    case 1:
      if ( ++Singletons > 1 ) Pass = false;
      break;
    case 2:
      if ( ++Doubletons > WldCount ) Pass = false;
    }
    if ( Pass == false ) break;
  }
  if ( Doubletons != WldCount ) Pass = false;
  if ( Pass ) {
    Singletons = 0;
    cocOldRank = ' ';
    for (i=0; i<DECK_SIZE; i++) {
      Pos1 = gHand[COMPUTER][i].Index;
      if ( Pos1 == EMPTY ) break;
      cocRank = gCard[Pos1].Title[0];
      if ( cocOldRank == ' ' ) {
        Singletons++;
        MeldPit = EMPTY;
        MeldPit = cFindMeldPit( cocRank );
        if ( MeldPit == EMPTY ) {
          switch (cocRank) {
          case '3': MeldPit =  0; break;
          case '4': MeldPit =  1; break;
          case '5': MeldPit =  2; break;
          case '6': MeldPit =  3; break;
          case '7': MeldPit =  4; break;
          case '8': MeldPit =  5; break;
          case '9': MeldPit =  6; break;
          case 'T': MeldPit =  7; break;
          case 'J': MeldPit =  8; break;
          case 'Q': MeldPit =  9; break;
          case 'K': MeldPit = 10; break;
          case 'A': MeldPit = 11; break;
          }
        }
        for ( j=0; j<MELD_DEPTH; i++) {
          Pos2 = gMeld[COMPUTER][MeldPit].Position[j];
          if ( Pos2 == EMPTY ) break;
        }
        gMeld[COMPUTER][MeldPit].Position[j] = Pos1;
        gHand[COMPUTER][i].Index = EMPTY;
        gHand[COMPUTER][i].Rank = '~';
        gHand[COMPUTER][i].Selected = false;
        gcHandCardCount--;
      }
      else {
        if ( cocRank == cocOldRank ) {
          Singletons++;
          gMeld[COMPUTER][MeldPit].Position[j] = Pos1;
          gHand[COMPUTER][i].Index = EMPTY;
          gHand[COMPUTER][i].Rank = '~';
          gHand[COMPUTER][i].Selected = false;
          gcHandCardCount--;
        }
        else {
          if ( Singletons == 2 ) {
            for ( k=0; k<DECK_SIZE; k++ ) {
              Pos2 = gHand[COMPUTER][k].Index;
              if ((gCard[Pos2].Title[0] == 'Z') ||
                  (gCard[Pos2].Title[0] == '2')) {
                gMeld[COMPUTER][MeldPit].Position[j] = Pos2;
                gHand[COMPUTER][k].Index = EMPTY;
                gHand[COMPUTER][k].Rank = '~';
                gHand[COMPUTER][k].Selected = false;
                gcHandCardCount--;
                break;
              }
            }
          }
          Singletons = 1;
          MeldPit = EMPTY;
          MeldPit = cFindMeldPit( cocRank );
          if ( MeldPit == EMPTY ) {
            switch (cocRank) {
            case '3': MeldPit =  0; break;
            case '4': MeldPit =  1; break;
            case '5': MeldPit =  2; break;
            case '6': MeldPit =  3; break;
            case '7': MeldPit =  4; break;
            case '8': MeldPit =  5; break;
            case '9': MeldPit =  6; break;
            case 'T': MeldPit =  7; break;
            case 'J': MeldPit =  8; break;
            case 'Q': MeldPit =  9; break;
            case 'K': MeldPit = 10; break;
            case 'A': MeldPit = 11; break;
            }
          }
          for ( j=0; j<MELD_DEPTH; i++) {
            Pos2 = gMeld[COMPUTER][MeldPit].Position[j];
            if ( Pos2 == EMPTY ) break;
          }
          gMeld[COMPUTER][MeldPit].Position[j] = Pos1;
          gHand[COMPUTER][i].Index = EMPTY;
          gHand[COMPUTER][i].Rank = '~';
          gHand[COMPUTER][i].Selected = false;
          gcHandCardCount--;
        }
      }
      cocOldRank = cocRank;
    }
    SortHand(COMPUTER);
  }

  return;
}

/*

This function enables the mouse environment while waiting for user
input.

*/

char far ReadDesktop() {
  int i=0;
  char KeyStroke[3] = "";
  bool Continuing=true;
  int SaveX=gMouseInformation.x;
  int SaveY=gMouseInformation.y;

  MouseOn( &gMouseInformation );
  while ( Continuing ) {
    KeyStroke[0] = KeyStroke[1] = KeyStroke[2] = 0x00;
    while ( kbhit() ) getch();
    while ( !kbhit() && !MouseHit( &gMouseInformation ) ) {
      if ((SaveX!=gMouseInformation.x)||(SaveY!=gMouseInformation.y)) {
        Gprintf( STATUS_LINE, 75, STATUS_FOR, STATUS_BACK, "%2d,%2d",
          gMouseInformation.y-1, gMouseInformation.x-1 );
      }
      SaveX = gMouseInformation.x;
      SaveY = gMouseInformation.y;
    }
    if ( kbhit() ) {
      KeyStroke[0] = getch();
      if ( KeyStroke[0] == 0x00 ) {
        KeyStroke[1] = getch();
        switch (KeyStroke[1]) {
        case 34: KeyStroke[0] = 'x'; break;
        case 24: KeyStroke[0] = 'y'; break;
        case 35: KeyStroke[0] = 'z';
        }
      }
      MouseOff( &gMouseInformation ); MouseOn( &gMouseInformation );
      Continuing = false;
    }
    if ( MouseHit( &gMouseInformation ) ) {
      MouseGet( &gMouseInformation );
      switch ( gMouseInformation.Button ) {
      case 1:
        for ( i=0; i<DESKTOP_BUTTON_COUNT; i++ ) {
          if (( gMouseInformation.y-1 >= gDesktop[gPhase][i].row1 ) &&
              ( gMouseInformation.y-1 <= gDesktop[gPhase][i].row2 ) &&
              ( gMouseInformation.x-1 >= gDesktop[gPhase][i].col1 ) &&
              ( gMouseInformation.x-1 <= gDesktop[gPhase][i].col2 ) ) {
            KeyStroke[0] = gDesktop[gPhase][i].letter;
            Continuing = false;
            break;
          }
        }
        if (Continuing) {
          KeyStroke[0] = 0x00;
          Continuing = false;
        }
        break;
      case 2:
        KeyStroke[0] = 0x1B;
        Continuing = false;
      }
    }
    // Otherwize continue
  }
  MouseOff( &gMouseInformation );
  if ( KeyStroke[0] ) {
    if ((KeyStroke[0] >= 'A') && (KeyStroke[0] <= 'Z')) {
      // lowercase
      KeyStroke[0] += ' ';
    }
  }

  return KeyStroke[0];
}

/*

This largely redundant function repeats the one above, but with respect
to a pull-down menu. The desktop is disabled while in this function.

*/

char far ReadMenu(cMenu *PullDown, int Entries) {
  int i=0;
  char KeyStroke[3];
  bool Continuing=true;

  ShowMenu(PullDown,Entries);
  MouseOn( &gMouseInformation );
  while ( Continuing ) {
    KeyStroke[0] = KeyStroke[1] = KeyStroke[2] = NULL;
    while ( kbhit() ) getch();
    while ( !kbhit() && !MouseHit( &gMouseInformation ) );
    if ( kbhit() ) {
      KeyStroke[0] = getch();
      if ( KeyStroke[0] == NULL ) KeyStroke[1] = getch();
      MouseOff( &gMouseInformation ); MouseOn( &gMouseInformation );
      Continuing = false;
    }
    if ( MouseHit( &gMouseInformation ) ) {
      MouseGet( &gMouseInformation );
      switch ( gMouseInformation.Button ) {
      case 1:
        for ( i=0; i<Entries; i++ ) {
          if (( gMouseInformation.y-1 >= PullDown[i].row1 ) &&
              ( gMouseInformation.y-1 <= PullDown[i].row2 ) &&
              ( gMouseInformation.x-1 >= PullDown[i].col1 ) &&
              ( gMouseInformation.x-1 <= PullDown[i].col2 ) ) {
            KeyStroke[0] = PullDown[i].letter;
            Continuing = false;
            break;
          }
        }
        if (Continuing) {
          KeyStroke[0] = 0x00;
          Continuing = false;
        }
        break;
      case 2:
        KeyStroke[0] = 0x1B;
        Continuing = false;
      }
    }
    // Otherwize continue
  }
  MouseOff( &gMouseInformation );
  if ( KeyStroke[0] ) {
    if ((KeyStroke[0] >= 'A') && (KeyStroke[0] <= 'Z')) {
      // lowercase
      KeyStroke[0] += ' ';
    }
  }
  HideMenu(PullDown,Entries);

  return KeyStroke[0];
}

/*

This function refreshes the screen from top to bottom.

*/

void far Refresh() {
  int i,j,a,N;

  i=j=a=N=0;
  cleardevice();

  /*

  Special case: Search for red threes in both hands to correct for
  taking pile with a red three at bottom from begining of round.

  */
  gcHandCardCount = 0;
  for (i=DECK_SIZE-1;i>=0;i--) {
    N = gHand[COMPUTER][i].Index;
    if (N != EMPTY) {
      gcHandCardCount++;
      if (IsRedThree(COMPUTER,N)) {
        gHand[COMPUTER][i].Index = EMPTY;
        gHand[COMPUTER][i].Rank = '~';
        gHand[COMPUTER][i].Selected = false;
        gcHandCardCount--;
        SortHand(COMPUTER);
      }
    }
  }
  gpHandCardCount = 0;
  for (i=DECK_SIZE-1;i>=0;i--) {
    N = gHand[PLAYER][i].Index;
    if (N != EMPTY) {
      gpHandCardCount++;
      if (IsRedThree(PLAYER,N)) {
        gHand[PLAYER][i].Index = EMPTY;
        gHand[PLAYER][i].Rank = '~';
        gHand[PLAYER][i].Selected = false;
        gpHandCardCount--;
        SortHand(PLAYER);
      }
    }
  }

  /*

  Computer Hand gHand0 -- only the bottom row card backs in two rows
  for 108 cards

  */

  for (i=DECK_SIZE-1;i>=54;i--) {
    N = gHand[COMPUTER][i].Index;
    if (N != EMPTY) {
      GetPixelsFromFile( gCardBackFileName, -7, (107-i)+18, false );
    }
  }
  for (i=53;i>=0;i--) {
    if (gHand[COMPUTER][i].Index != EMPTY) {
#ifdef TESTING
// Face up display of hand
      DisplayCard(gHand[COMPUTER][i].Index, -8, i*2, false);
#else
      GetPixelsFromFile( gCardBackFileName, -9, (53-i)+18, false );
#endif
    }
  }

  // Computer Melds -- all threes as Meld0

  ShowMelds(COMPUTER,5);

  // Score Pad -- showing written bonus and melds

  ShowScore();

  // Stock -- with number of cards left

  Gprintf(STOCK_ROW-1,STOCK_COLUMN+3,YELLOW,BLACK,"%3d",
    gNextCardInStock+1);
  if (gNextCardInStock >= 0) {
    GetPixelsFromFile( "DECKSIDE.PXL",    STOCK_ROW, STOCK_COLUMN-1,
      false );
    GetPixelsFromFile( gCardBackFileName, STOCK_ROW, STOCK_COLUMN,
      false );
  }

  // Discard Pile -- with wilds and red threes sideways

  if (gTopPile <= EMPTY) gTopPile = EMPTY; // bug fix
  for (i=0;i<DECK_SIZE;i++) {
    a = gDiscard[i];
    if (a == EMPTY) break;
    else {
      if (gCard[a].IsWild) {
        DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,true);
      }
      else {
        if ((gCard[a].Title[0] == '3') &&
           ((gCard[a].Title[1] == 'H') ||
            (gCard[a].Title[1] == 'D'))) {
          DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,true);
        }
        else DisplayCard(a,STOCK_ROW,STOCK_COLUMN+9,false);
      }
    }
  }
  Gprintf(STOCK_ROW-1,STOCK_COLUMN+10,YELLOW,BLACK,"%3d",
    gTopPile+1);

  // Player Melds -- all threes as Meld0

  ShowMelds(PLAYER,37);

  /*

  Player Hand -- five rows for 108 cards, last row is hardly ever
  used. The cards have a small designation in the upper right corner.

  */

  for (i=1;i<=5;i++) {
    for (j=(22*(i-1));j<(22*i);j++) {
      if (j>=DECK_SIZE) break;
      if (gHand[PLAYER][j].Index != EMPTY) {
        DisplayCard(gHand[PLAYER][j].Index, STATUS_LINE-(6-i),
          (((22*i)-j-1)*3)+7, false);
      }
    }
  }

  // Status Line -- showing all currents

  Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK, "%80.80s"," " );
  if (gpMeldedBefore) {
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK,
      " Round %d |", gRounds );
  } else {
    Gprintf(STATUS_LINE, 0,STATUS_FOR,STATUS_BACK,
      " Round %d | first meld = %d |", gRounds, (pCalcFirstMeld()) );
  }
  Gprintf(STATUS_LINE,50,STATUS_FOR,STATUS_BACK, "%s (%s)", PROGNAME,
    VERSION );

  // Desktop Menu Bar

  Gprintf( 0, 0, BLACK, WHITE, "%80.80s"," " );
  for (i=0;i<DESKTOP_BUTTON_COUNT;i++) {
    Gprintf(gDesktop[gPhase][i].row1,gDesktop[gPhase][i].col1,BLACK,
      WHITE, "%s", gDesktop[gPhase][i].caption );
    Gprintf(gDesktop[gPhase][i].row1,gDesktop[gPhase][i].col1+1,RED,
      WHITE, "%c", gDesktop[gPhase][i].caption[1] );
  }

  // Check if Player or Computer is out, or if the Stock is empty.

  if (gpHandCardCount <= 0)      gEndRound = true;
  if (gcHandCardCount <= 0)      gEndRound = true;
  if (gNextCardInStock == EMPTY) gEndRound = true;
}

/*

This function restores pixels behind a pull-down menu from a file.

*/

void far RestoreBehindWindow(char *FileName, int Top, int Left,
       int Bottom, int Right) {
  int i, j;
  int PixelTop = Top*gTextHeight;
  int PixelLeft = Left*gTextWidth;
  int PixelBottom = ((Bottom+1)*gTextHeight)-1;
  int PixelRight = ((Right+1)*gTextWidth)-1;
  FILE *InFile;
  char InChar = ' ';

  i=j=0;
  if ( (InFile = fopen(FileName, "rb")) == NULL ) {
    ProgramDestructor();
    printf("Error in %s: Cannot open %s file.\n", PROGNAME, FileName);
    exit( 2 );
  }

  for (i=PixelTop;i<=PixelBottom;i++) {
    for (j=PixelLeft;j<=PixelRight;j++) {
      InChar = fgetc( InFile );
      switch (InChar) {
      case '0': putpixel(j,i, 0); break;
      case '1': putpixel(j,i, 1); break;
      case '2': putpixel(j,i, 2); break;
      case '3': putpixel(j,i, 3); break;
      case '4': putpixel(j,i, 4); break;
      case '5': putpixel(j,i, 5); break;
      case '6': putpixel(j,i, 6); break;
      case '7': putpixel(j,i, 7); break;
      case '8': putpixel(j,i, 8); break;
      case '9': putpixel(j,i, 9); break;
      case 'A': putpixel(j,i,10); break;
      case 'B': putpixel(j,i,11); break;
      case 'C': putpixel(j,i,12); break;
      case 'D': putpixel(j,i,13); break;
      case 'E': putpixel(j,i,14); break;
      default : putpixel(j,i,15);
      }
    }
  }
  fclose(InFile);
}

/*

This function restores the state of the computer to file.

*/

void far RestoreStateOfComputer() {
  FILE *in;
  int i,j,k;

  in = fopen("SAVESTAT.DTA","rb");

// Card Deck

  for (i=0;i<DECK_SIZE;i++) {
    fgets(s,80,in);
    gCard[i].Shuffle[0] = s[0];
    gCard[i].Shuffle[1] = s[1];
    gCard[i].Shuffle[2] = s[2];
    gCard[i].Shuffle[3] = s[3];
    gCard[i].Title[0] = s[4];
    gCard[i].Title[1] = s[5];
    gCard[i].Title[2] = s[6];
    gCard[i].Rank = s[7];
    gCard[i].Suit = s[8];
    s[0] = s[9];
    s[1] = s[10];
    s[2] = s[11];
    s[3] = 0x00;
    gCard[i].Value = atoi(s);
    if (s[12] == 'T')
         gCard[i].IsWild = true;
    else gCard[i].IsWild = false;
  }

// Hands

  gpHandCardCount = 0;
  gcHandCardCount = 0;
  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<DECK_SIZE;j++) {
      fgets(s,80,in);
      gHand[i][j].Rank = s[0];
      s[0] = s[1];
      s[1] = s[2];
      s[2] = s[3];
      s[3] = 0x00;
      gHand[i][j].Index = atoi(s);
      if (s[4] == 'T')
           gHand[i][j].Selected = true;
      else gHand[i][j].Selected = false;
      if (i == PLAYER) gpHandCardCount++;
      if (i == COMPUTER) gcHandCardCount++;
    }
  }

// Top Discard Pile

  fgets(s,80,in);
  s[3] = 0x00;
  gTopPile = atoi(s);

// Stock

  for (i=0;i<DECK_SIZE;i++) {
    fgets(s,80,in);
    s[3] = 0x00;
    gStock[i] = atoi(s);
  }

// Discard Pile

  for (i=0;i<DECK_SIZE;i++) {
    fgets(s,80,in);
    s[3] = 0x00;
    gDiscard[i] = atoi(s);
  }

// Melds and Red Trey

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<MELD_LOCATIONS;j++) {
      fgets(s,80,in);
      if (s[0] == 'T')
           gMeld[i][j].IsBook = true;
      else gMeld[i][j].IsBook = false;
      if (s[1] == 'T')
           gMeld[i][j].HasWild = true;
      else gMeld[i][j].HasWild = false;
      for (k=0;k<MELD_DEPTH;k++) {
        s[0] = s[(k*3)+2];
        s[1] = s[(k*3)+3];
        s[2] = s[(k*3)+4];
        s[3] = 0x00;
        gMeld[i][j].Position[k] = atoi(s);
      }
    }
  }

// Score

  for (i=0;i<MAX_ROUNDS;i++) {
    fgets(s,80,in);
    s[60] = s[5];
    s[61] = s[6];
    s[62] = s[7];
    s[63] = s[8];
    s[64] = s[9];
    s[5] = 0x00;
    gBonusPoints[i][0] = atoi(s);
    s[0] = s[60];
    s[1] = s[61];
    s[2] = s[62];
    s[3] = s[63];
    s[4] = s[64];
    s[5] = 0x00;
    gBonusPoints[i][1] = atoi(s);
    fgets(s,80,in);
    s[60] = s[5];
    s[61] = s[6];
    s[62] = s[7];
    s[63] = s[8];
    s[64] = s[9];
    s[5] = 0x00;
    gMeldPoints[i][0] = atoi(s);
    s[0] = s[60];
    s[1] = s[61];
    s[2] = s[62];
    s[3] = s[63];
    s[4] = s[64];
    s[5] = 0x00;
    gMeldPoints[i][1] = atoi(s);
    fgets(s,80,in);
    s[60] = s[5];
    s[61] = s[6];
    s[62] = s[7];
    s[63] = s[8];
    s[64] = s[9];
    s[5] = 0x00;
    gScore[i][0] = atoi(s);
    s[0] = s[60];
    s[1] = s[61];
    s[2] = s[62];
    s[3] = s[63];
    s[4] = s[64];
    s[5] = 0x00;
    gScore[i][1] = atoi(s);
  }

// Miscellaneous

  fgets(s,80,in);
  if (s[0] == 'T')
       gcMeldedBefore = true;
  else gcMeldedBefore = false;
  if (s[1] == 'T')
       gpMeldedBefore = true;
  else gpMeldedBefore = false;
  s[0] = s[2];
  s[1] = s[3];
  s[2] = s[4];
  s[3] = 0x00;
  gNextCardInStock = atoi(s);
  s[0] = s[5];
  s[1] = s[6];
  s[2] = s[7];
  s[3] = 0x00;
  gRounds = atoi(s);
  fclose(in);
  Refresh();
}

/*

This function saves the state of the computer to file.

*/

void far SaveStateOfComputer() {
  FILE *out;
  int i,j,k;

  out = fopen("SAVESTAT.DTA","wb");

// Card Deck

  for (i=0;i<DECK_SIZE;i++) {
    fprintf(out,"%c",gCard[i].Shuffle[0]);
    fprintf(out,"%c",gCard[i].Shuffle[1]);
    fprintf(out,"%c",gCard[i].Shuffle[2]);
    fprintf(out,"%c",gCard[i].Shuffle[3]);
    fprintf(out,"%c",gCard[i].Title[0]);
    fprintf(out,"%c",gCard[i].Title[1]);
    fprintf(out,"%c",gCard[i].Title[2]);
    fprintf(out,"%c",gCard[i].Rank);
    fprintf(out,"%c",gCard[i].Suit);
    fprintf(out,"%3.1d",gCard[i].Value);
    if (gCard[i].IsWild)
         fprintf(out,"T\r\n");
    else fprintf(out,"F\r\n");
  }

// Hands

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<DECK_SIZE;j++) {
      fprintf(out,"%c",gHand[i][j].Rank);
      fprintf(out,"%3.1d",gHand[i][j].Index);
      if (gHand[i][j].Selected)
           fprintf(out,"T\r\n");
      else fprintf(out,"F\r\n");
    }
  }

// Top Discard Pile

  fprintf(out,"%3.1d\r\n",gTopPile);

// Stock

  for (i=0;i<DECK_SIZE;i++)
    fprintf(out,"%3.1d\r\n",gStock[i]);

// Discard Pile

  for (i=0;i<DECK_SIZE;i++)
    fprintf(out,"%3.1d\r\n",gDiscard[i]);

// Melds and Red Trey

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<MELD_LOCATIONS;j++) {
      if (gMeld[i][j].IsBook)
           fprintf(out,"T");
      else fprintf(out,"F");
      if (gMeld[i][j].HasWild)
           fprintf(out,"T");
      else fprintf(out,"F");
      for (k=0;k<MELD_DEPTH;k++)
        fprintf(out,"%3.1d",gMeld[i][j].Position[k]);
      fprintf(out,"\r\n");
    }
  }

// Score

  for (i=0;i<MAX_ROUNDS;i++) {
    for (j=0;j<NUM_PLAYERS;j++) {
      fprintf(out,"%5.1d",gBonusPoints[i][j]);
    }
    fprintf(out,"\r\n");
    for (j=0;j<NUM_PLAYERS;j++) {
      fprintf(out,"%5.1d",gMeldPoints[i][j]);
    }
    fprintf(out,"\r\n");
    for (j=0;j<NUM_PLAYERS;j++) {
      fprintf(out,"%5.1d",gScore[i][j]);
    }
    fprintf(out,"\r\n");
  }

// Miscellaneous

  if (gcMeldedBefore)
       fprintf(out,"T");
  else fprintf(out,"F");
  if (gpMeldedBefore)
       fprintf(out,"T");
  else fprintf(out,"F");
  fprintf(out,"%3.1d",gNextCardInStock);
  fprintf(out,"%3.1d\r\n",gRounds);
  fclose(out);
}

/*

This function saves pixels behind a pull-down menu into a file.

*/

void far SaveBehindWindow(char *FileName, int Top, int Left,
          int Bottom, int Right) {
  int i, j, ColorBuffer;
  int PixelTop = Top*gTextHeight;
  int PixelLeft = Left*gTextWidth;
  int PixelBottom = ((Bottom+1)*gTextHeight)-1;
  int PixelRight = ((Right+1)*gTextWidth)-1;
  FILE *OutFile;
  char OutChar=' ';

  i=j=ColorBuffer=0;
  OutFile = fopen(FileName, "wb");
  for (i=PixelTop;i<=PixelBottom;i++) {
    for (j=PixelLeft;j<=PixelRight;j++) {
      ColorBuffer = getpixel(j,i);
      switch (ColorBuffer) {
      case  0: OutChar = '0'; break;
      case  1: OutChar = '1'; break;
      case  2: OutChar = '2'; break;
      case  3: OutChar = '3'; break;
      case  4: OutChar = '4'; break;
      case  5: OutChar = '5'; break;
      case  6: OutChar = '6'; break;
      case  7: OutChar = '7'; break;
      case  8: OutChar = '8'; break;
      case  9: OutChar = '9'; break;
      case 10: OutChar = 'A'; break;
      case 11: OutChar = 'B'; break;
      case 12: OutChar = 'C'; break;
      case 13: OutChar = 'D'; break;
      case 14: OutChar = 'E'; break;
      default: OutChar = 'F';
      }
      fputc( OutChar, OutFile );
    }
  }
  fclose(OutFile);
}

/*

This function returns EMPTY or index in hand for selected occurance.

*/

int far SelectCardInHand(int who, char a) {
  int i,b;

  i=b=0;
  for (;i<DECK_SIZE;i++) {
    b = gHand[who][i].Index;
    if (b != EMPTY) {
      if (gCard[b].Title[0] == a) {
        if (!(gHand[who][i].Selected)) {
          gHand[who][i].Selected = true;
          return i;
        }
      }
    }
  }

  return EMPTY;
}

/*

This function involves the complicated procedure of displaying the
melds of a given side.

*/

void far ShowMelds(int Who, int Row) {
  int i,j,a;

  i=j=a=0;
  if (Who == COMPUTER) gcCanastaCount = 0;
  if (Who == PLAYER) gpCanastaCount = 0;
  for (i=0;i<MELD_LOCATIONS;i++) {
    gMeld[Who][i].IsBook = false;
    gMeld[Who][i].HasWild = false;
    for (j=0;j<MELD_DEPTH;j++) {
      a = gMeld[Who][i].Position[j];
      if (a == EMPTY) break;
      if (gCard[a].IsWild) gMeld[Who][i].HasWild = true;
    }
    if (j>=7) gMeld[Who][i].IsBook = true;
  }
  for (i=MELD_LOCATIONS-1;i>=1;i--) {
    if (gMeld[Who][i].IsBook) {
      if (gMeld[Who][i].HasWild) {

// Black canasta

        for (j=0;j<MELD_DEPTH;j++) {
          a = gMeld[Who][i].Position[j];
          if (gCard[a].IsWild) {
            DisplayCard(a,Row+4,i*6, false);
            break;
          }
        }
        for (j=0;j<MELD_DEPTH;j++) {
          a = gMeld[Who][i].Position[j];
          if (!(gCard[a].IsWild)) {
            DisplayCard(a,Row+5,i*6, false);
            break;
          }
        }
      }
      else {

// Red canasta

        for (j=0;j<MELD_DEPTH;j++) {
          a = gMeld[Who][i].Position[j];
          if (!(gCard[a].IsWild)) {
            if ((gCard[a].Suit == 'H') || (gCard[a].Suit == 'D')) {
              DisplayCard(a,Row+5,i*6, false);
              break;
            }
          }
        }
      }
      GetPixelsFromFile("DECKSIDE.PXL",Row+5,(i*6)-1, false );
      if (Who == COMPUTER) gcCanastaCount++;
      if (Who == PLAYER) gpCanastaCount++;
    }
    else {

// Non-canasta

      for (j=0;j<6;j++) {
        if (gMeld[Who][i].Position[j] == EMPTY) break;
        DisplayCard(gMeld[Who][i].Position[j], j+Row, i*6, false );
      }
    }
  }
  for (j=0;j<8;j++) {

// Threes

    if (gMeld[Who][0].Position[j] != EMPTY) {
      DisplayCard(gMeld[Who][0].Position[j], j+Row, 0, false );
    }
  }
}

/*

This function displays a specified menu with specified number of
entries.

*/

void far ShowMenu(cMenu *PullDown, int Entries) {
  int i=0;
  int MenuWidth = strlen(PullDown[0].caption);
  int Top = PullDown[0].row1-1;
  int Left = PullDown[0].col1-1;
  int Bottom = PullDown[Entries-1].row1+1;
  int Right = PullDown[Entries-1].col1+MenuWidth;

  SaveBehindWindow("MENUBACK.DTA", Top, Left, Bottom+1, Right+1);
  Gprintf(Top, Left, BLACK, WHITE, "Ú");
  for (i=0;i<MenuWidth;i++ )
    Gprintf(Top, PullDown[0].col1+i, BLACK, WHITE, "Ä");
  Gprintf(Top, PullDown[0].col1+MenuWidth, BLACK, WHITE, "¿");
  for (i=0;i<Entries;i++) {
    Gprintf(PullDown[i].row1, PullDown[i].col1-1, BLACK, WHITE, "³");
    Gprintf(PullDown[i].row1, PullDown[i].col1, BLACK, WHITE,
      "%*.*s", MenuWidth, MenuWidth, PullDown[i].caption);
    Gprintf(PullDown[i].row1, PullDown[i].col1+MenuWidth,
      BLACK, WHITE, "³%c",0xB2);
    Gprintf(PullDown[i].row1, PullDown[i].col1+1,
      RED, WHITE, "%c", PullDown[i].caption[1]);
  }
  Gprintf(Bottom, Left, BLACK, WHITE, "À");
  for (i=1;i<=MenuWidth;i++ )
    Gprintf(Bottom, Left+i, BLACK, WHITE, "Ä");
  Gprintf(Bottom, Right, BLACK, WHITE, "Ù%c",0xB2);
  for (i=1;i<=MenuWidth+2;i++ )
    Gprintf(Bottom+1, Left+i, BLACK, WHITE, "%c",0xB2);
}

/*

This function displays the running table of scores.

*/

void far ShowScore() {
  int i;

  if (gRounds<=1) return;
  Gprintf(STOCK_ROW-1, 1,YELLOW,BLACK,"    Player | Computer");
  for (i=1;i<gRounds;i++) {
    if (gScore[i-1][PLAYER] == 0) break;
    Gprintf(STOCK_ROW+(i*4)-4, 1,YELLOW,BLACK,"B:");
    Gprintf(STOCK_ROW+(i*4)-4, 3,YELLOW,BLACK,"%9.1d",
      gBonusPoints[i-1][PLAYER]);
    Gprintf(STOCK_ROW+(i*4)-4,12,YELLOW,BLACK,"|%9.1d",
      gBonusPoints[i-1][COMPUTER]);
    Gprintf(STOCK_ROW+(i*4)-3, 1,YELLOW,BLACK,"M:");
    Gprintf(STOCK_ROW+(i*4)-3, 3,YELLOW,BLACK,"%9.1d",
      gMeldPoints[i-1][PLAYER]);
    Gprintf(STOCK_ROW+(i*4)-3,12,YELLOW,BLACK,"|%9.1d",
      gMeldPoints[i-1][COMPUTER]);
    Gprintf(STOCK_ROW+(i*4)-2, 1,YELLOW,BLACK,"  ---------|---------");
    Gprintf(STOCK_ROW+(i*4)-1, 1,YELLOW,BLACK,"T:");
    Gprintf(STOCK_ROW+(i*4)-1, 3,YELLOW,BLACK,"%9.1d",
      gScore[i-1][PLAYER]);
    Gprintf(STOCK_ROW+(i*4)-1,12,YELLOW,BLACK,"|%9.1d",
      gScore[i-1][COMPUTER]);
  }
}

/*

This function shuffles the deck.

*/

void far ShuffleDeck() {
  int i;

  for (i=0;i<DECK_SIZE;i++) {
    sprintf(record[i]  ,"%3.3s",gCard[i].Shuffle);
    sprintf(record[i]+3,"%2.2s",gCard[i].Title);
    sprintf(record[i]+5,"%c",gCard[i].Rank);
    sprintf(record[i]+6,"%c",gCard[i].Suit);
    sprintf(record[i]+7,"%2d",gCard[i].Value);
    if (gCard[i].IsWild)
         sprintf(record[i]+9,"T");
    else sprintf(record[i]+9,"F");
    record[i][10] = 0x00;
  }

  qsort((void *)record, DECK_SIZE, sizeof(record[0]), sort_function);

  for (i=0;i<DECK_SIZE;i++) {
    gCard[i].Shuffle[0] = record[i][0];
    gCard[i].Shuffle[1] = record[i][1];
    gCard[i].Shuffle[2] = record[i][2];
    gCard[i].Title[0] = record[i][3];
    gCard[i].Title[1] = record[i][4];
    gCard[i].Rank = record[i][5];
    gCard[i].Suit = record[i][6];
    if (record[i][9] == 'T')
         gCard[i].IsWild = true;
    else gCard[i].IsWild = false;
    if (record[i][7] == ' ') s[0] = '0'; else s[0] = record[i][7];
    if (record[i][8] == ' ') s[1] = '0'; else s[1] = record[i][8];
    s[2] = 0x00;
    gCard[i].Value = atoi(s);
  }
}

/*

This function sorts the specified hand.

*/

void far SortHand(int who) {
  int i;

  for (i=0;i<DECK_SIZE;i++) {
    sprintf(record[i],"%c",gHand[who][i].Rank);
    if (gHand[who][i].Index == EMPTY)
         sprintf(record[i]+1,"999");
    else sprintf(record[i]+1,"%3d",gHand[who][i].Index);
    if (gHand[who][i].Selected)
         sprintf(record[i]+4,"T");
    else sprintf(record[i]+4,"F");
    record[i][5] = 0x00;
  }

  qsort((void *)record, DECK_SIZE, sizeof(record[0]), sort_function);

  for (i=0;i<DECK_SIZE;i++) {
    gHand[who][i].Rank = record[i][0];
    if (record[i][4] == 'T')
         gHand[who][i].Selected = true;
    else gHand[who][i].Selected = false;
    if (record[i][1] == ' ') s[0] = '0'; else s[0] = record[i][1];
    if (record[i][2] == ' ') s[1] = '0'; else s[1] = record[i][2];
    if (record[i][3] == ' ') s[2] = '0'; else s[2] = record[i][3];
    s[3] = 0x00;
    gHand[who][i].Index = atoi(s);
    if (gHand[who][i].Index == 999) gHand[who][i].Index = EMPTY;
  }
}

/*

This function starts a new round.

*/

void far StartOver() {
  int i,j,k;

  i=j=k=0;

  // Reset global variables

  NextCardBack();
  gNextCardInStock = DECK_SIZE-1;
  gTopPile = k = EMPTY;
  gEndRound = false;
  gChanged = true;
  gPhase = 0;
// 08Nov2010 Next two lines added
  gpMeldedBefore = false;
  gcMeldedBefore = false;

  // Create Card Deck.

  for (i=0; i<DECK_SIZE-4; i++ ) {
    j = i%13;
    itoa(rand() % RAND_MAX,gCard[i].Shuffle,36);
    gCard[i].Title[0] = gRankString[j];
    gCard[i].Rank = 'a'+(13-j);
    if (j == 0) {
      k++;
      k %= 4;
    }
    gCard[i].Title[1] = gSuitString[k];
    gCard[i].Title[2] = 0x00;
    gCard[i].Suit = gSuitString[k];
    switch (gCard[i].Title[0]) {
    case '3': case '4': case '5': case '6': case '7':
      gCard[i].Value = 5;
      gCard[i].IsWild = false;
      break;
    case '8': case '9': case 'T': case 'J': case 'Q': case 'K':
      gCard[i].Value = 10;
      gCard[i].IsWild = false;
      break;
    case 'A':
      gCard[i].Value = 20;
      gCard[i].IsWild = false;
      break;
    case '2':
      gCard[i].Value = 20;
      gCard[i].IsWild = true;
      break;
    }
  }

  // Add jokers

  for (; i<DECK_SIZE; i++ ) {
    itoa(rand() % RAND_MAX,gCard[i].Shuffle,36);
    gCard[i].Title[0] = 'Z';
    if ((i%2) == 0)
      gCard[i].Title[1] = '1';
    else
      gCard[i].Title[1] = '2';
    gCard[i].Title[2] = 0x00;
    gCard[i].Rank = 'a';
    gCard[i].Suit = '*';
    gCard[i].Value = 50;
    gCard[i].IsWild = true;
  }

  ShuffleDeck();

  // Clear the Table.

  for (i=0;i<NUM_PLAYERS;i++) {
    for (j=0;j<MELD_LOCATIONS;j++) {
      gMeld[i][j].IsBook = false;
      gMeld[i][j].HasWild = false;
      for (k=0;k<MELD_DEPTH;k++) {
        gMeld[i][j].Position[k] = EMPTY;
      }
    }
  }
  for (i=0;i<DECK_SIZE;i++) {
    gStock[i] = i;
    gDiscard[i] = EMPTY;
    gHand[COMPUTER][i].Index = EMPTY;
    gHand[COMPUTER][i].Rank = '~';
    gHand[COMPUTER][i].Selected = false;
    gHand[PLAYER][i].Index = EMPTY;
    gHand[PLAYER][i].Rank = '~';
    gHand[PLAYER][i].Selected = false;
  }

  // Deal

  gpHandCardCount = 0;
  gcHandCardCount = 0;
  for (i=0;i<15;i++) {
    for (j=0;j<NUM_PLAYERS;j++) {
      gHand[j][i].Index = DrawCard(j);
      gHand[j][i].Rank = gCard[gHand[j][i].Index].Rank;
      if (j == PLAYER)   gpHandCardCount++;
      if (j == COMPUTER) gcHandCardCount++;
    }
  }
  SortHand(COMPUTER);
  SortHand(PLAYER);

  // Turn up first upcard from stock

  gTopPile++;
  gDiscard[gTopPile] = gStock[gNextCardInStock];
  gStock[gNextCardInStock] = EMPTY;
  gNextCardInStock--;
}

/*

This function checks for wild or three on discard pile, asks user
for a meld, checks meld, sorts hand, moves all discard pile to hand,
erases discard pile, and forces a "draw card" if illegal meld.

*/

bool far pTake() {
  int i,d;
  char a,b;

  i=d=0;
  a=b=' ';
  if (!(gpMeldedBefore)) return false;
  if (gTopPile == EMPTY) return false;
  b = gCard[gDiscard[gTopPile]].Title[0];

  switch (b) {
  case 'Z':
  case '2':
  case '3':
    return false;
  }
  a = pMeld(true);
  if (a == ' ') return false;
  if (!(pMinLegalMeld(true))) return false;
  if (a == b) {
    for (i=0;i<DECK_SIZE;i++) {
      if (gHand[PLAYER][i].Index == EMPTY) {
        break;
      }
    }
    for (;;) {
      d = gDiscard[gTopPile];
      gDiscard[gTopPile] = EMPTY;
      gTopPile--;
      gHand[PLAYER][i].Index = d;
      gHand[PLAYER][i].Rank = gCard[d].Rank;
      gHand[PLAYER][i].Selected = false;
      gpHandCardCount++;
      if (gTopPile == EMPTY) break;
      i++;
    }
    SortHand(PLAYER);
  }
  else {
    pDraw();
    return true;
  }
  return true;
}

/*

This function tries to take the discard pile using the computer hand.

*/

bool far cTryTakeDiscard() {
  int CardList[20];
  int i, j, k;
  int MeldPit;
  int NaturalList[8];
  char NaturalToMeld = gCard[gDiscard[gTopPile]].Title[0];
  int NatInHand = 0;
  char RankOfCardInList;
  int Score = gCard[gDiscard[gTopPile]].Value;
  int WildList[12];
  int WldInHand = 0;
  int DeckIndex;

  if (gTopPile == EMPTY) return false;
  switch ( NaturalToMeld ) {
  case 'Z':
  case '2':
  case '3':
    return false;
  }
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) return false;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    if ( RankOfCardInList == NaturalToMeld ) break;
  }
  for (i=0; i<MELD_DEPTH; i++) CardList[i] = EMPTY;
  for (i=0; i<8; i++) NaturalList[i] = EMPTY;
  for (i=0; i<12; i++) WildList[i] = EMPTY;
  NaturalList[0] = gDiscard[gTopPile];
  MeldPit = cFindMeldPit( NaturalToMeld );
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
    RankOfCardInList = gCard[DeckIndex].Title[0];
    switch ( RankOfCardInList ) {
    case 'Z':
    case '2':
      WildList[WldInHand++] = DeckIndex;
    }
    if ( RankOfCardInList == NaturalToMeld )
      NaturalList[++NatInHand] = DeckIndex;
  }
  if ( gWildInDiscardPile ) {
    if ( MeldPit == EMPTY ) {
      if ( NatInHand < 2 ) return false;
    }
  }
  else {
    if ( MeldPit == EMPTY ) {
      if ( WldInHand >= 1 ) {
        WldInHand = 1;
        NatInHand = 1;
      }
      else {
        if ( NatInHand < 2 )  return false;
        else {
          NatInHand = 2;
        }
      }
    }
  }
  for (i=0; i<NatInHand; i++) {
    DeckIndex = NaturalList[i+1];
    if ( DeckIndex == EMPTY ) break;
    CardList[i] = DeckIndex;
    Score += gCard[DeckIndex].Value;
  }
  for ( j=0; j<WldInHand; j++ ) {
    DeckIndex = WildList[j];
    if ( DeckIndex == EMPTY ) break;
    CardList[i + j] = DeckIndex;
    Score += gCard[DeckIndex].Value;
  }
  if ( !gcMeldedBefore ) {
    if ( Score >= cMinLegalMeld() ) {
      if (( NatInHand + WldInHand ) >= 2 )
        gcMeldedBefore = true;
      else return false;
    }
    else return false;
  }
  if ( MeldPit == EMPTY ) {
    switch (NaturalToMeld) {
    case '3': MeldPit= 0; break;
    case '4': MeldPit= 1; break;
    case '5': MeldPit= 2; break;
    case '6': MeldPit= 3; break;
    case '7': MeldPit= 4; break;
    case '8': MeldPit= 5; break;
    case '9': MeldPit= 6; break;
    case 'T': MeldPit= 7; break;
    case 'J': MeldPit= 8; break;
    case 'Q': MeldPit= 9; break;
    case 'K': MeldPit=10; break;
    case 'A': MeldPit=11; break;
    }
  }
  for (i=0; i<MELD_DEPTH; i++) {
    DeckIndex = gMeld[COMPUTER][MeldPit].Position[i];
    if ( DeckIndex == EMPTY ) break;
  }
  for ( j=0; j<WldInHand; j++ ) {
    DeckIndex = WildList[j];
    if ( DeckIndex == EMPTY ) break;
    gMeld[COMPUTER][MeldPit].Position[i+j] = DeckIndex;
    gMeld[COMPUTER][MeldPit].HasWild = true;
  }
  for ( k=0; k<=NatInHand; k++ ) {
    DeckIndex = NaturalList[k];
    if ( DeckIndex == EMPTY ) break;
    gMeld[COMPUTER][MeldPit].Position[i+j+k] = DeckIndex;
  }
  for (i=0; i<20; i++) {
    if ( CardList[i] == EMPTY ) break;
    for ( j=0; j<DECK_SIZE; j++ ) {
      DeckIndex = gHand[COMPUTER][j].Index;
      if ( DeckIndex == CardList[i] ) break;
    }
    gHand[COMPUTER][j].Index = EMPTY;
    gHand[COMPUTER][j].Rank = '~';
    gHand[COMPUTER][j].Selected = false;
    gcHandCardCount--;
  }
  gDiscard[gTopPile] = EMPTY;
  gTopPile--;
  for (i=0; i<DECK_SIZE; i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if ( DeckIndex == EMPTY ) break;
  }
  for ( j=0; j<=DECK_SIZE; j++ ) {
    DeckIndex = gDiscard[j];
    if ( DeckIndex == EMPTY ) break;
    gHand[COMPUTER][i+j].Index = DeckIndex;
    gHand[COMPUTER][i+j].Rank = gCard[DeckIndex].Rank;
    gHand[COMPUTER][i+j].Selected = false;
    gcHandCardCount++;
    gDiscard[j] = EMPTY;
  }
  gTopPile = EMPTY;
  gWildInDiscardPile = false;
  SortHand(COMPUTER);

  return true;
}

/*

This function is used to wait exactly the seconds specified.

*/

void far WaitASec() {
   time_t T, Tsave;

   T = time( NULL );
   Tsave = T + 1.75;
   while ( Tsave > T ) T = time( NULL );
}

/*

This function returns where a card is located in the computer hand.

*/

int far cWhereInHand( int Object ) {
  int i;
  int Result = EMPTY;
  int DeckIndex;

  for (i=0;i<DECK_SIZE;i++) {
    DeckIndex = gHand[COMPUTER][i].Index;
    if (DeckIndex == EMPTY) break;
    if (DeckIndex == Object) {
      Result = i;
      break;
    }
  }

  return Result;
}

/* ***************************************************************** */

/*

This function constructs the time zone, the graphic environment, random
number sequencing, the mouse environment, and the scorepad.

*/

void far ProgramConstructor() {
  int i,j,GraphError;
  int GraphDevice = VGA;
  int GraphMode = VGAHI;

  i=j=GraphError=0;
  putenv("TZ=PST8PDT");
  tzset();

  initgraph( &GraphDevice, &GraphMode, PATH_TO_BGI );
  GraphError = graphresult();
  if( GraphError != grOk ){
    pd2();
    printf("Path to BGI files: \"%s\".\n", PATH_TO_BGI );
    printf("Graphics error in %s:\n", PROGNAME);
    printf("%s\nPress a key to continue...\n",
      grapherrormsg( GraphError ) );
    getch();
    exit( 5 );
  }
  settextstyle(DEFAULT_FONT, HORIZ_DIR, 1);
  gTextHeight = textheight( "H" );
  gTextWidth = textwidth( "M" );

  srand((unsigned) time(NULL));

  MouseInit( &gMouseInformation );
  if ( !gMouseInformation.Exist ) {
    ProgramDestructor();
    printf("Error in %s: The mouse does not exist.\n", PROGNAME);
    printf("The mouse is needed for this program.\n");
    printf("Press a key to continue...\n");
    getch();
    exit( 6 );
  }
  for (i=0;i<MAX_ROUNDS;i++) {
    for (j=0;j<NUM_PLAYERS;j++) {
      gBonusPoints[i][j] = 0;
      gMeldPoints[i][j]  = 0;
      gScore[i][j]       = 0;
    }
  }
  StartOver();
}

/*

This function is the main loop. It refreshes the graphic screen 
if changed, processes the end of round and the end of game, reads
the desktop menu from the user, and processes the desktop menu
options.

*/

bool far MainLoop() {
  char Answer[3] = "  ";

  if (gChanged) Refresh();
  gChanged = false;
  if (gEndRound) {
    FigureScore(gRounds-1);
    Refresh();
    Gprintf( 0, 1, BLACK, WHITE, " End of Round               ");
    Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... ");
    gRounds++;
    ShowScore();
    getch();
    if (gEndGame) {
      cleardevice();
      Gprintf( 0, 1, BLACK, WHITE, " End of Game!               ");
      Gprintf( 1, 1, BLACK, WHITE, " Press a key to continue... ");
      ShowScore();
      getch();
      return false;
    }
    StartOver();
    Refresh();
    Gprintf( 1, 1, BLACK, WHITE, " New Round                  ");
  }
  Answer[0] = ReadDesktop();
  switch (Answer[0]) {
  case 0x1B: // Esc
  case 'e': // Exit
    ProgramDestructor();
    exit( 7 );
    break;
  case 'h': // Help
    Answer[1] = ReadMenu(gHelpMenu,HELP_PULLDOWN_COUNT);
    if (Answer[1] == 'a') About();
    gChanged = true;
    break;
  default:
    switch (gPhase) {
    case 0:
      switch (Answer[0]) {
      case 't': // Take
        if (pTake()) gPhase = 1;
        /* Failure to take repeats Phase 0 */
        gChanged = true;
        break;
      case 'd': // Draw
        if (pDraw()) gPhase = 1;
        /* Failure to draw repeats Phase 0 */
        gChanged = true;
        break;
      case 'r': // Restore
        RestoreStateOfComputer();
        break;
      case 's': // Save
        SaveStateOfComputer();
        break;
      }
      break;
    case 1:
      switch (Answer[0]) {
      case 'm': // Meld
        pMeld(false);
        gChanged = true;
        break;
      case 'd': // Discard
        if (pDiscard()) ComputerTurn();
        gChanged = true;
        break;
      }
      break;
    }
  }

  return true;
}

/*

This function closes the graphic environment and clears the text screen.

*/

void far ProgramDestructor() {
  closegraph();
  pd2();
}

/*

This function is the partial destructor that clears the text screen.

*/

void far pd2() {
  textmode( C4350 );
  textcolor( LIGHTGRAY );
  textbackground( BLACK );
  clrscr();
}

/*

This function assists the qsort function call.

*/

int far sort_function( const void *a, const void *b) {
   return( strcmp((char *)a,(char *)b) );
}

// END OF FILE: GCANASTA.CPP


```

---

### Post by decoherence on 2011-07-15
You will have better luck getting responses if you post this in the programming section of the forum. :)

---

### Post by machdohvah on 2011-07-15
> **decoherence said:**
> You will have better luck getting responses if you post this in the programming section of the forum. :)

OK, will do.

---

