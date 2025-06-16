<html><head></head><body><h1>📘 Pick&amp;Tell Project Wiki</h1>
<blockquote>
<p>AI-powered personalized fairy tale generation service for children</p>
</blockquote>
<hr>
<h2>Project Overview</h2>
<p><strong>Pick&amp;Tell</strong> is a personalized AI-powered storytelling service that generates stories in text, image, and audio formats based on a child's choices.</p>
<ul>
<li>
<p><strong>Backend</strong>: Python Django</p>
</li>
<li>
<p><strong>Frontend</strong>: HTML, CSS, JavaScript</p>
</li>
<li>
<p><strong>Tech Stack</strong>: ChatGPT (OpenAI), ElevenLabs TTS, Stable Diffusion, Mubert BGM</p>
</li>
<li>
<p><strong>Features</strong>:</p>
<ul>
<li>
<p>Text-based story generation based on user input</p>
</li>
<li>
<p>Emotion-based TTS audio synthesis</p>
</li>
<li>
<p>AI-generated images with consistent character appearance</p>
</li>
<li>
<p>Branching structure via user choices</p>
</li>
<li>
<p>Automatic discussion card generation for parent-child interaction</p>
</li>
</ul>
</li>
</ul>
<hr>
<h2>💡 Motivation &amp; Startup Plan</h2>
<h3> Problems Identified</h3>
<ul>
<li>
<p>Existing children's content is often rigid with pre-made stories and illustrations</p>
</li>
<li>
<p>Lack of personalized content tailored to the child's imagination, preferences, or age</p>
</li>
</ul>
<h3> Limitations of Existing Solutions</h3>
<ul>
<li>
<p>Predominantly passive content (videos, audiobooks)</p>
</li>
<li>
<p>Lack of interaction and self-directed storytelling experience</p>
</li>
</ul>
<h3> Market Size &amp; Trends</h3>
<ul>
<li>
<p><strong>Global digital children's content market</strong>: Approx. $11 billion (as of 2023)</p>
</li>
<li>
<p><strong>Korean digital children's content market</strong>: Approx. ₩200 billion</p>
</li>
<li>
<p><strong>Global interactive story app market</strong>: Expected CAGR of 12% (2024–2028)</p>
</li>
<li>
<p>Post-COVID surge in demand for at-home, personalized content due to remote learning and increase in dual-income households</p>
</li>
</ul>
<h3> Applicable Market Opportunities</h3>
<ul>
<li>
<p>Domestic and global edtech platforms (e.g., Woongjin Book Club)</p>
</li>
<li>
<p>AI-based English learning apps, interactive e-books, smart toy integrations</p>
</li>
</ul>
<h3> Opportunity Summary</h3>
<ul>
<li>
<p>Combining GPT for text, Stable Diffusion for visuals, and ElevenLabs for voice allows immersive storytelling</p>
</li>
<li>
<p>User-driven branching logic provides differentiated self-directed learning experience</p>
</li>
</ul>
<h3> 3C Analysis</h3>

Category | Description
-- | --
Customer | Parents of children aged 3–10 / Early childhood education institutions
Competitor | Standard story apps (e.g., Todo Math, YouTube Kids) – limited interactivity
Company | Differentiated via AI-based interactive storytelling, multimodal consistency (image + voice)


<h3> STP Strategy</h3>
<ul>
<li>
<p><strong>Segmentation</strong>: Preschoolers (3–6), Children (7–10), ESL learners</p>
</li>
<li>
<p><strong>Targeting</strong>: Parents interested in premium educational content / Educational institutions</p>
</li>
<li>
<p><strong>Positioning</strong>: “The AI fairy tale maker that brings your child’s imagination to life”</p>
</li>
</ul>
<h3> 4P Marketing Mix</h3>
<ul>
<li>
<p><strong>Product</strong>: Interactive AI-generated stories / Multilingual support / Character continuity</p>
</li>
<li>
<p><strong>Price</strong>: Free basic service + Premium features (story saving, character customization)</p>
</li>
<li>
<p><strong>Place</strong>: Web, iOS &amp; Android apps, B2B partnerships with kindergartens and education platforms</p>
</li>
<li>
<p><strong>Promotion</strong>: Parenting communities, YouTube influencer collaborations, education trial campaigns</p>
</li>
</ul>
<hr>
<h2> Installation &amp; Environment</h2>
<h3> Python Environment</h3>
<pre><code class="language-bash">Python 3.10 or higher recommended
pip install -r requirements.txt
</code></pre>
<h3> Key Dependencies</h3>
<pre><code class="language-text">Django==5.0.6
openai
requests==2.32.3
elevenlabs==1.13.4
langdetect
python-dotenv
opencv-python
Pillow
pydantic==2.10.3
</code></pre>
<blockquote>
<p>See <code inline="">requirements.txt</code> for full list</p>
</blockquote>
<hr>
<h2> API Endpoints</h2>
<h3><code inline="">/generate_story/</code> (POST)</h3>
<ul>
<li>
<p>Accepts user inputs (age, gender, genre, characters) and returns two scenes (text + image + audio)</p>
</li>
<li>
<p>The second scene includes two branching choices (A/B)</p>
</li>
</ul>
<h3><code inline="">/branch_story/</code> (POST)</h3>
<ul>
<li>
<p>Generates new story scenes based on the selected choice (up to 2 branches)</p>
</li>
<li>
<p>Final branch concludes the story and includes parent-child discussion cards</p>
</li>
</ul>
<h3><code inline="">/set_current_index/</code> (POST)</h3>
<ul>
<li>
<p>Saves the current scene index to session</p>
</li>
</ul>
<h3><code inline="">/show_page/&lt;page_idx&gt;/</code> (GET)</h3>
<ul>
<li>
<p>Displays the selected story page (text + image + audio)</p>
</li>
</ul>
<hr>
<h2> Example Code</h2>
<h3> Python Example</h3>
<pre><code class="language-python">import requests

res = requests.post("http://localhost:8000/generate_story/", data={
    "age": 6,
    "gender": "girl",
    "genre": "adventure",
    "characters[]": ["rabbit", "cat"]
})
print(res.status_code)
</code></pre>
<h3> JavaScript Branching Example</h3>
<pre><code class="language-javascript">fetch('/branch_story/', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    choice_index: 1
  })
})
.then(res =&gt; res.json())
.then(data =&gt; console.log(data))
</code></pre>
<hr>
<h2> Technical Overview</h2>
<ul>
<li>
<p><strong>OpenAI GPT</strong>:</p>
<ul>
<li>
<p>Story content and branching logic generation</p>
</li>
<li>
<p>Prompt translation for image generation</p>
</li>
<li>
<p>Parent-child discussion card generation</p>
</li>
</ul>
</li>
<li>
<p><strong>Stable Diffusion API</strong>:</p>
<ul>
<li>
<p>Scene-based image generation</p>
</li>
<li>
<p>Maintains character visual consistency using facial reference</p>
</li>
</ul>
</li>
<li>
<p><strong>ElevenLabs TTS</strong>:</p>
<ul>
<li>
<p>Emotionally rich scene narration in audio format</p>
</li>
</ul>
</li>
<li>
<p><strong>Mubert (Optional)</strong>:</p>
<ul>
<li>
<p>Generates background music based on genre</p>
</li>
</ul>
</li>
</ul>
<hr>
<h2>🔒 Content Moderation</h2>
<ul>
<li>
<p>Combined OpenAI Moderation API and K-Hate dataset-based filtering</p>
</li>
<li>
<p>Filters inappropriate language and adjusts sensitivity by age group</p>
</li>
</ul>
<hr>
<h2> File Storage Structure</h2>
<ul>
<li>
<p><code inline="">MEDIA_ROOT/images/</code>: Generated images</p>
</li>
<li>
<p><code inline="">MEDIA_ROOT/audios/</code>: TTS audio files</p>
</li>
<li>
<p><code inline="">MEDIA_ROOT/storylines/</code>: Complete story JSON per session</p>
</li>
<li>
<p><code inline="">MEDIA_ROOT/reference/</code>: Facial reference images</p>
</li>
<li>
<p><code inline="">MEDIA_ROOT/bgm/</code>: Background music files</p>
</li>
</ul>
<hr>
<h2> Session Storage Keys</h2>
<ul>
<li>
<p><code inline="">pages</code>: Story pages (text, image, audio, choices)</p>
</li>
<li>
<p><code inline="">user_info</code>: Age, gender, genre, characters</p>
</li>
<li>
<p><code inline="">current_idx</code>: Currently active scene index</p>
</li>
<li>
<p><code inline="">reference_face</code>: Path to reference face image</p>
</li>
<li>
<p><code inline="">sd_base_seed</code>: Shared seed for Stable Diffusion</p>
</li>
</ul>
<hr>
