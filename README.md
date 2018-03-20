# branchPrediction
Optimized GShare branch prediction header file to reduce MPKI of different benchmarks. Original source code obtained from http://hpca23.cse.tamu.edu/taco/camino/cbp2/. Original source code was intended for the 2nd JILP Championship Branch Prediction Competition on September 14th, 2006.

Major optimizations to GShare file (my_predictor.h):
  (1) Implemented a modified tournament branch predictor that would determine, for each branch, if the branch prediction for that branch could be determined more accurately from just the local history of that branch or from a combination of the local and global history.
  (2) Implemented a pseudo-perceptron approach to global history length of past branches using a weighted function of the two previous times a single branch instruction was taken to determine whether to use a global history of the last 2 branch instructions, of the last 15 branch instructions, or of the last 30 branch instructions for the next branch prediction of that branch instruction. This is because the predictions for some branch instructions can be determined on if the previous branch in the global history was taken or not taken while others may depend on more than just the previous instruction. 
  
Minor optimizations to GShare file:
  (1) Changed the local history table to include 30 entries instead of 15 entries.
  (2) Changed 2-bit saturating counter to 3 bit saturating counter to determine if a branch was taken or not. Changed incrementation of counter to be 2 instead of 1 (i.e. incremented by 2 instead of 1 or decremented by 2 instead of 1 if not taken).
