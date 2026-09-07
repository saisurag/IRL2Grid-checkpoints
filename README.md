# IRL2Grid-checkpoints

Trained model checkpoints for https://github.com/saisurag/IRL2Grid

MSc Advanced Computing, Imperial College London

Supervisor: Dr. Francesco Leofante

With the exception of the original teacher PPO oracles, the original code repository excludes '*.tar' through its '.gitignore', in consideration of storage. Instead, all trained .tar checkpoints are provided in this repository. They can also be downloaded via the following Google Drive link:

      https://drive.google.com/file/d/1Pb0b8U6JRertQdG9igteh-RTTkOoG417/view?usp=drive_link

Every file is a PyTorch archive written by 'common/checkpoint.py' and read by 'honest_eval_any.py'.

## Layout

The tree mirrors the code repository; every run occupies the same path in both repositories. In IRL2Grid, the directory holds the logs and visualisations, whereas this repository holds the .tar archive. All contents are available under 'IRL2Grid-checkpoints/'.

    IRL2Grid-checkpoints/
        checkpoints/    the PPO teachers every reported result distils from
        April-Runs/     tests run during the month of April
        May-Runs/       tests run during the month of May
        June-Runs/      tests run during the month of July, focusing primarily on DTPO
        July-Runs/      tests run during the month of July, during which defects were observed and fixed
        Final-Results/  the final tests run during July and August, which form the basis of the thesis

## Naming Convention

The 'Final-Results/' directory is named as follows:

      <grid>_<method>_<leaves>_<seed>

Each directory contains 'checkpoint/<name>.tar'. 

The filename is built via 'main.py' as follows:

     {alg}_{grid}_{T|R}_{seed}_{difficulty}_{H}_{I}_{C1|C2}_{unix time}_{tag}.tar

T|R: Action space, either Topology (T) or Redispatch (R)
H: Heuristic wraps the policy
I: Heuristic is idle
C1|C2: Constrained variants

## How to use this archive

Clone this repository next to the IRL2Grid code repository. When using the evaluator to reproduce results, point the checkpoint path to this folder as follows:

      python honest_eval_any.py --ckpt ../IRL2Grid-checkpoints/Final-Results/hpc/runs/bus14_dtpo-full_L16_s100/checkpoint/*.tar --total 80

## Note

Run data from April to July is kept as a record of the work done. Data within these directories have not been reported or used for the thesis, which reports 'Final-Results/' only.
