# Lab-5_202001039
Git Repository for Lab 5

Tool Used MyPy

Errornous Code:
```
import imp
from tkinter import *
import tkinter.messagebox
from PIL import Image, ImageTk
import socket, threading, sys, traceback, os
from RtpPacket import RtpPacket
import time 


CACHE_FILE_NAME = "cache-"

CACHE_FILE_EXT = ".jpg"
```
Error Flagged:
```
client.py:4: error: Library stubs not installed for "PIL"  [import]
client.py:4: note: Hint: "python3 -m pip install types-Pillow"
client.py:4: note: (or run "mypy --install-types" to install all missing stub packages)
client.py:4: note: See https://mypy.readthedocs.io/en/stable/running_mypy.html#missing-imports
client.py:4: error: Name "Image" already defined (possibly by an import)  [no-redef]
Found 2 errors in 1 file (checked 1 source file)    
```

Analysis:
The above import errors are false positive these get flagged because mypy was not able to find the module you are trying to import, whether it comes bundled with type hints or not there are not actual errors as these libraries were in fact imported and used in the program.

Errornous Code:
```
self.serverAddr = serveraddr
self.serverPort = int(serverport)
self.rtpPort = int(rtpport)
self.fileName = filename
self.rtspSeq = 0
self.sessionId = 0
self.requestSent = -1
self.teardownAcked = 0
self.connectToServer()
self.frameNbr = 0
#new variables for stat calculation
self.statExpRtpNb = 0 
self.statCumLost = 0
self.lastHighSeqNb = 0  
self.statTotalPlayTime = 0 
self.statTotalBytes = 0 
self.statDataRate = 0
self.statFractionLost = 0
self.lastCumLost = 0
```

Errors Flagged:
```
client.py:34:2: C0103: Attribute name "serverAddr" doesn't conform to snake_case naming style (invalid-name)                                                            client.py:35:2: C0103: Attribute name "serverPort" doesn't conform to snake_case naming style (invalid-name)
client.py:36:2: C0103: Attribute name "rtpPort" doesn't conform to snake_case naming style (invalid-name)
client.py:37:2: C0103: Attribute name "fileName" doesn't conform to snake_case naming style (invalid-name)
client.py:38:2: C0103: Attribute name "rtspSeq" doesn't conform to snake_case naming style (invalid-name)
client.py:39:2: C0103: Attribute name "sessionId" doesn't conform to snake_case naming style (invalid-name)
client.py:40:2: C0103: Attribute name "requestSent" doesn't conform to snake_case naming style (invalid-name)
client.py:41:2: C0103: Attribute name "teardownAcked" doesn't conform to snake_case naming style (invalid-name)
client.py:43:2: C0103: Attribute name "frameNbr" doesn't conform to snake_case naming style (invalid-name)
client.py:45:2: C0103: Attribute name "statExpRtpNb" doesn't conform to snake_case naming style (invalid-name)
client.py:46:2: C0103: Attribute name "statCumLost" doesn't conform to snake_case naming style (invalid-name)
client.py:47:2: C0103: Attribute name "lastHighSeqNb" doesn't conform to snake_case naming style (invalid-name)
client.py:48:2: C0103: Attribute name "statTotalPlayTime" doesn't conform to snake_case naming style (invalid-name)
client.py:49:2: C0103: Attribute name "statTotalBytes" doesn't conform to snake_case naming style (invalid-name)
client.py:50:2: C0103: Attribute name "statDataRate" doesn't conform to snake_case naming style (invalid-name)
client.py:51:2: C0103: Attribute name "statFractionLost" doesn't conform to snake_case naming style (invalid-name)
client.py:52:2: C0103: Attribute name "lastCumLost" doesn't conform to snake_case naming style (invalid-name)
client.py:118:3: C0103: Attribute name "statStartTime" doesn't conform to snake_case naming style (invalid-name)
client.py:121:3: C0103: Attribute name "playEvent" doesn't conform to snake_case naming style (invalid-name)
client.py:204:2: C0103: Attribute name "rtspSocket" doesn't conform to snake_case naming style (invalid-name)
client.py:248:2: C0103: Attribute name "numPktsExpected" doesn't conform to snake_case naming style (invalid-name)
client.py:249:2: C0103: Attribute name "numPktsLost" doesn't conform to snake_case naming style (invalid-name)
client.py:315:2: C0103: Attribute name "rtpSocket" doesn't conform to snake_case naming style (invalid-name)     
```

Analysis:
Naming style errors are true positives but naming style convention depends from programmer from programmer there are many naming styles like pascal case, snake case, kebab case, camel case. If the codebas has been using a specific naming style since the beginning then it does not make sense to change it later to snake case naming style that mypy specifically expects in the code.

Errornous code:
```
	INIT = 0
	READY = 1
	PLAYING = 2
```

Errors Flagged:
```
client.py:18:0: W0311: Bad indentation. Found 1 spaces, expected 4 (bad-indentation)
client.py:19:0: W0311: Bad indentation. Found 1 spaces, expected 4 (bad-indentation)
client.py:20:0: W0311: Bad indentation. Found 1 spaces, expected 4 (bad-indentation) 
```

Analysis:
Its a good practice to use tab space (4 whitespaces in code) mypy rightfully flags this particualar thing. This is not some error that breaks the code it's just about good programming practice that makes one's code easily readable and understandable and helps keep track of braces and what code block belongs to which section.

Errors Flagged:
```
Unused import(s) sys, enum, types, TclError, re, wantobjects, TkVersion, TclVersion, READABLE, WRITABLE, EXCEPTION, EventType, Event, NoDefaultRoot, Variable, StringVar, IntVar, DoubleVar, BooleanVar, mainloop, getint, getdouble, getboolean, Misc, CallWrapper, XView, YView, Wm, Tk, Tcl, Pack, Place, Grid, BaseWidget, Widget, Toplevel, Canvas, Checkbutton, Entry, Frame, Listbox, Menu, Menubutton, Message, Radiobutton, Scale, Scrollbar, Text, OptionMenu, PhotoImage, BitmapImage, image_names, image_types, Spinbox, LabelFrame, PanedWindow, NO, FALSE, OFF, YES, TRUE, ON, NW, SW, NE, SE, NS, EW, NSEW, CENTER, NONE, X, Y, BOTH, LEFT, TOP, RIGHT, BOTTOM, RAISED, SUNKEN, FLAT, RIDGE, GROOVE, SOLID, HORIZONTAL, VERTICAL, NUMERIC, CHAR, WORD, BASELINE, INSIDE, OUTSIDE, SEL, SEL_FIRST, SEL_LAST, END, INSERT, CURRENT, ANCHOR, ALL, NORMAL, DISABLED, ACTIVE, HIDDEN, CASCADE, CHECKBUTTON, COMMAND, RADIOBUTTON, SEPARATOR, SINGLE, BROWSE, MULTIPLE, EXTENDED, DOTBOX, UNDERLINE, PIESLICE, CHORD, ARC, FIRST, LAST, BUTT, PROJECTING, ROUND, BEVEL, MITER, MOVETO, SCROLL, UNITS and PAGES from wildcard import of tkinter (unused-wildcard-import)
```

Analysis: It is not good to import libraries that one does not intend to use, it leads to unnecessary memory consumption and high compile time. One should import only the necessary libraries. This is also not some critical error its just about good programming practice.

