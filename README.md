RecastNavigationDelphi
======================

Port of Recast Navigation into Delphi 

**Source code location:**
   https://github.com/memononen/recastnavigation


**Source code version:**
   Around 01 Nov 2014


**Porting guidelines:**
 - RecastNavigationDelphi is a straight clone of RecastNavigation with as little changes as possible, to allow to keep projects synced in the future.
 - Any changes/improvements to the lib functionality should be first included into C++ master to avoid separation.
 - RND follows RN structure very closely, except for GUI stuff, which is VCL for simplicity instead of imGUI RN solution.
 - All file names are the same, but with an "RN_" prefix. 
 - Some units were split to avoid circular dependencies, they are called RN_UnitNameHelper.


**Hints about the code:**
 - Multi-condition "for" loops and loops where iterator gets changed inside the loop, were converted to while/repeat loops. Loop code needs to be repeated before any "continue".
 - Move method first two arguments *(Src, Dst)* need to be swapped in Delphi.
 - Delphi needs to wrap overflowing manipulations with a *{$O}* directive to supress errors.
 - Delphi needs manual disposal of objects created within record , as they dont have built-in destructor support in them.
 - To simplify the pointer trickery, *{$POINTERMATH ON}* had to be enabled almost in every unit.
 - Typed @ operator setting is great help, but sadly it does not work sometimes.

 
**Common pitfalls during porting:**
 - Passing argument *@SomePointer* instead of *SomePointer*. Typed @ helps to catch those, but not always.
 - Calling *Move/FillChar* methods without swapping arguments places.
 - Writing *for .. to .. do* loop instead of *for .. downto .. do* in rare cases.
 - 

**Todos:**
 - Fix plethora of memory leaks around the code.
 - TempObstacles demo.
 - Some parts are commented out, waiting to be ported.
 - Sync with current state of the source code.
