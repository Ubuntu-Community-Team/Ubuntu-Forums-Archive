---
title: "Error In Anki"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-05-22
I installed the language learning application anki! i got the following error while downloading the decs for the anki! How to rectify these error!

thank you?


Debug info:
Traceback (most recent call last):
  File "/usr/share/anki/ankiqt/ui/main.py", line 716, in loadDeck
    self.deck = DeckStorage.Deck(deckPath)
  File "/usr/share/anki/anki/deck.py", line 2814, in Deck
    deck.rebuildQueue()
  File "/usr/share/anki/anki/deck.py", line 685, in rebuildQueue
    self.checkDue()
  File "/usr/share/anki/anki/deck.py", line 665, in checkDue
    stmt % 0, now=time.time()+self.delay0).rowcount
  File "/usr/share/anki/anki/db.py", line 114, in statement
    return self.execute(text(sql), kwargs)
  File "/usr/share/anki/anki/db.py", line 90, in execute
    x = self._session.execute(*a, **ka)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/orm/session.py", line 753, in execute
    clause, params or {})
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 824, in execute
    return Connection.executors[c](self, object, multiparams, params)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 874, in _execute_clauseelement
    return self.__execute_context(context)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 896, in __execute_context
    self._cursor_execute(context.cursor, context.statement, context.parameters[0], context=context)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 950, in _cursor_execute
    self._handle_dbapi_exception(e, statement, parameters, cursor, context)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 931, in _handle_dbapi_exception
    raise exc.DBAPIError.instance(statement, parameters, e, connection_invalidated=is_disconnect)
OperationalError: (OperationalError) no such index: ix_cards_priorityDue u'update cards  indexed by ix_cards_priorityDue set isDue = 1 where type = 0 and isDue = 0 and priority in (1,2,3,4) and combinedDue <= ?' [1306071730.21912]

---

