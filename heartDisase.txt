fis=mamfis('Name','heart_disease');

fis=addInput(fis,[0,190],'Name',"ldl");
fis=addInput(fis,[0,100],'Name',"age");
fis=addInput(fis,[0,220],'Name',"bloodPressure");
fis=addInput(fis,[100,250],'Name',"cholesterol");
fis=addInput(fis,[0,120],'Name',"bloodSugar");
fis=addInput(fis,[0,70],'Name',"hdl");
fis=addOutput(fis,[0,45],'Name',"risk");


fis = addMF(fis,"age","trapmf",[-30 -5 30 40],'Name',"young");
fis = addMF(fis,"age","trapmf",[30 40 50 60],'Name',"mid");
fis = addMF(fis,"age","trapmf",[50 60 100 100],'Name',"old");

fis = addMF(fis,"bloodPressure","trapmf",[-30 -5 100 120],'Name',"low");
fis = addMF(fis, "bloodPressure","trapmf",[100 120 140 160],'Name',"mid");
fis = addMF(fis,"bloodPressure","trapmf",[140 160 180 200],'Name',"high");
fis = addMF(fis,"bloodPressure","trapmf",[180 200 220 220],'Name',"veryHigh");

fis = addMF(fis,"cholesterol","trapmf",[-30 -5 180 200],'Name',"low");
fis = addMF(fis,"cholesterol","trapmf",[180 200 220 240],'Name',"mid");
fis = addMF(fis,"cholesterol","trapmf",[220 240 250 270],'Name',"high");

fis = addMF(fis,"bloodSugar","trimf",[90 120 130],'Name',"veryHigh");


fis = addMF(fis,"ldl","trimf",[0 0 100],'Name',"normal");
is = addMF(fis,"ldl","trimf",[100 130 160],'Name',"limit");
fis = addMF(fis,"ldl","trimf",[130 160 190],'Name',"high");
fis = addMF(fis,"ldl","trapmf",[160 190 200 230],'Name',"veryHigh");

fis = addMF(fis,"hdl","trapmf",[0 0 30 40],'Name',"low");
fis = addMF(fis,"hdl","trapmf",[30 40 50 60],'Name',"mid");
fis = addMF(fis,"hdl","trapmf",[50 60 80 100],'Name',"high");


mf1 = fismf("trapmf",[0 0 5 10],'Name',"not");
mf2 = fismf("trapmf",[5 10 15 20],'Name',"little");
mf3 = fismf("trapmf",[15 20 25 30],'Name',"mid");
mf4 = fismf("trapmf",[25 30 35 40],'Name',"high");
mf5 = fismf("trapmf",[35 40 45 50],'Name',"veryHigh");

fis.Outputs(1).MembershipFunctions = [mf1 mf2 mf3 mf4 mf5];



% fis = addMF(fis,"risk","trapmf",[0 0 5 10],'Name',"not");
% fis = addMF(fis,"risk","trapmf",[5 10 15 20],'Name',"little");
% fis = addMF(fis,"risk","trapmf",[15 20 25 30],'Name',"mid");
% fis = addMF(fis,"risk","trapmf",[25 30 35 40],'Name',"high");
% fis = addMF(fis,"risk","trapmf",[35 40 45 50],'Name',"veryHigh");


rulelist=[0 1 1 0 1 3 1 1 1;
0 1 1 0 2 3 2 1 1;
0 1 1 0 3 3 3 1 1;
0 1 1 0 4 3 4 1 1;
0 2 1 0 0 3 1 1 1;
1 2 2 0 0 0 1 1 1;
2 2 2 0 0 0 1 1 1;
3 2 2 0 0 0 1 1 1;
1 3 2 0 0 0 3 1 1;
2 3 3 0 0 0 4 1 1;
3 3 3 0 0 0 5 1 1;
1 2 1 0 1 1 1 1 1;
1 0 0 1 0 0 2 1 1;
2 0 0 1 0 0 4 1 1;
3 0 0 1 0 0 5 1 1;
1 1 1 1 1 3 2 1 1;
2 1 1 1 1 3 4 1 1;
3 1 1 1 1 3 5 1 1;
2 1 1 1 4 3 5 1 1;
0 4 3 0 4 3 5 1 1;
0 3 3 0 3 2 5 1 1;
1 4 2 0 4 2 3 1 1;
2 4 0 0 0 0 5 1 1;
3 4 0 0 0 0 5 1 1];

%fis=addRule(fis,rulelist);
%plotfis(fis);
%plotmf(fis,'input',1,191);
%plotmf(fis,'input',2,101);
%plotmf(fis,'input',3,221);
%plotmf(fis,'input',4,251);
%plotmf(fis,'input',5,121);
%plotmf(fis,'input',6,71);
plotmf(fis,'output',1,46);
