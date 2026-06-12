---
title: "class hierarchy of chess pieces on the basis of increasing levels of moves"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by manish411 on 2011-09-02
I have a question. I have to design a class hierarchy based on the basis of different moves 
of chess pieces in the increasing levels of moves.
Please suggest your ideas.

---

### Post by muteXe on 2011-09-02
Well the simplest is just an abstract data class called 'Piece' with a virtual Move() method in it. Then have all the real pieces derive from this and override the Move() method. Not really a hierarchy as such, but it would work.

---

### Post by obatala on 2011-09-02
Hell Manish411;
          iam new here this is my first post so bear with me. Iam an avid chess player i play
          on freechess.org I play at 2100 Expert level.Iam interested in learning to program C
          and anything dealing with chess.So about your question.I think the problem is that it
          as my limited understanding is not defined properly.HumanvsMachine Move analisis
         (Now iam assuming u are working on the "next move" part of prog)

           Human                                                COMPUTER
   number of good moves                        number of possible moves
             A    B   C   D  E                           A  B C D E F G I iNFINITE
   


       IF :    Move "A"  Then           If:   Move "B" Then      If:  Move "C" Then
                                                         
Moves:       X      Y       Z       Moves: X        Y       Z      Moves: X    Y      Z
     
      A   B    C   D   E   F   G  

Moves:


Moves:          
IN HUMAN CHESS WE CALL THIIS TREE OF  ANALISIS 
IN COM PROG IS CALLED A PLY I BILIEVE EVERY LEVEL MOVES:
 

IS THIS WHAT U TALKING ABOUT LET ME HEAR FOR YOU.

---

