# OSCE Minsk Group Statements Bot

## Read the statements [here](http://osceminskgroupbot.github.io/) and follow the bot [on Twitter](https://twitter.com/MinskGroupBot).

Statements are generated using the awesome [char-rnn](https://github.com/karpathy/char-rnn) by [Andrej Karpathy](https://twitter.com/karpathy/). We trained Justin Johnson's [torch-rnn](https://github.com/jcjohnson/torch-rnn) implementation on the original [OSCE Minsk Group statements](http://www.osce.org/press-releases?filters=+im_taxonomy_vid_1:(434)) (~200KB English text) using the following parameters:

    th train.lua -rnn_size 512 -dropout 0.5 -input_h5 ../bot/minskgroup/20160406.h5 -input_json ../bot/minskgroup/20160406.json
    
Statements are generated at quite low temperature (probably because of the small training set it doesn't learn very well):

    th sample.lua -length 4000 -temperature 0.5 -start_text "VIENNA, 7 April 2016" -checkpoint ../bot/minskgroup/cv/s512d0.5_3400.t7
    
The model is available in the repository.
