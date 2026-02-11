<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>DOSA File Registry System</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; }
    table { border-collapse: collapse; width: 100%; margin-bottom: 20px; }
    th, td { border: 1px solid #ccc; padding: 8px; text-align: left; }
    th { background: #f0f0f0; }
    button { padding: 6px 10px; cursor: pointer; }
    .hidden { display: none; }
    .year-folder { background: #eef; padding: 10px; margin-top: 10px; }
    .actions { color: #0066cc; font-weight: bold; }
  </style>
</head>
<body>

<h2>FILE REGISTRY</h2>
<p><strong>S/NO | File Name | File Index</strong></p>
<div id="fileRegistryContainer">
  <!-- This container will be dynamically populated -->
</div>
<script>
/* ==============================
   File Registry Universal Script
   ============================== */

/* Example: Offices list (can match your main table S/NO list) */
const offices = [
  { id: 'vc', name: "Vice-Chancellor's Office" },
  { id: 'dvasa', name: "DVC (ASA)'s Office" },
  { id: 'dvaaf', name: "DVC (A & F)'s Office" },
  { id: 'dvpre', name: "DVC (PRE)'s Office" },
  // Add all other offices here with unique IDs
];

/* Example: documents database (date format: YYYY-MM-DD) */
const documentsDB = {
  dvasa: [
    { date: '2026-02-10', name: 'Staff Meeting Minutes', index: 'UoE/B/DOSA/DVASA/002/001' },
    { date: '2026-02-05', name: 'Performance Report', index: 'UoE/B/DOSA/DVASA/002/002' },
    { date: '2026-01-28', name: 'Budget Request', index: 'UoE/B/DOSA/DVASA/002/003' },
  ],
  vc: [
    { date: '2026-02-08', name: 'VC Circular', index: 'UoE/B/DOSA/VC/001/001' },
    { date: '2026-01-30', name: 'Annual Report', index: 'UoE/B/DOSA/VC/001/002' },
  ],
  // Add documents for other offices
};

/* =============================
   Render File Registry
   ============================= */
function renderFileRegistry(officeId) {
  const container = document.getElementById('fileRegistryContainer');
  const office = offices.find(o => o.id === officeId);
  const docs = documentsDB[officeId] || [];

  let html = `
    <h2>${office.name} File Registry</h2>
    
    <!-- Year Selection -->
    <div class="year-selection">
      <label for="academicYear">Select Academic Year:</label>
      <select id="academicYear" onchange="renderDocuments('${officeId}')">
        <option value="2025/2026">Academic Year 2025/2026</option>
        <option value="2024/2025">Academic Year 2024/2025</option>
        <option value="2023/2024">Academic Year 2023/2024</option>
      </select>
      <button onclick="renderDocuments('${officeId}')">Open Year</button>
    </div>

    <!-- Search Bar -->
    <div class="search-bar">
      <input type="text" id="documentSearch" placeholder="Search documents..." onkeyup="searchDocuments()">
    </div>

    <!-- Documents Table -->
    <table id="documentsTable" border="1" cellspacing="0" cellpadding="5">
      <thead>
        <tr>
          <th>Date</th>
          <th>Document Name</th>
          <th>File Index</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody id="documentsBody">
        <!-- Documents will be populated here -->
      </tbody>
    </table>

    <button onclick="backToFileList()">⬅ Back to File List</button>
  `;

  container.innerHTML = html;

  // Initially render documents
  renderDocuments(officeId);
}

/* =============================
   Populate Documents Table
   ============================= */
function renderDocuments(officeId) {
  const docs = documentsDB[officeId] || [];
  const tbody = document.getElementById('documentsBody');

  // Sort latest first
  const sortedDocs = docs.sort((a, b) => new Date(b.date) - new Date(a.date));

  let rows = '';
  sortedDocs.forEach(doc => {
    rows += `
      <tr>
        <td>${new Date(doc.date).toLocaleDateString()}</td>
        <td>${doc.name}</td>
        <td>${doc.index}</td>
        <td><button onclick="openDocument('${doc.index}')">Open</button></td>
      </tr>
    `;
  });

  tbody.innerHTML = rows;
  searchDocuments(); // Apply current search filter
}

/* =============================
   Search Documents
   ============================= */
function searchDocuments() {
  const input = document.getElementById('documentSearch');
  const filter = input.value.toLowerCase();
  const table = document.getElementById('documentsTable');
  const tr = table.getElementsByTagName('tr');

  for (let i = 1; i < tr.length; i++) { // skip header
    const td = tr[i].getElementsByTagName('td')[1]; // document name column
    if (td) {
      const txtValue = td.textContent || td.innerText;
      tr[i].style.display = txtValue.toLowerCase().includes(filter) ? '' : 'none';
    }
  }
}

/* =============================
   Document Open & Navigation
   ============================= */
function openDocument(docIndex) {
  alert('Opening document: ' + docIndex);
  // Replace with actual document open logic
}

function backToFileList() {
  const container = document.getElementById('fileRegistryContainer');
  container.innerHTML = ''; // Clear registry
  alert('Returning to main file list...');
  // Optionally, render your main table here
}

/* =============================
   Example: Open DVC (ASA) Registry
   ============================= */
// Call this function when user clicks the office button
// Example: renderFileRegistry('dvasa');
</script>

<table>
  <tr>
    <th>S/NO</th>
    <th>File Name</th>
    <th>File Index</th>
    <th>Action</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Vice-Chancellor’s Office</td>
    <td>UoE/B/DOSA/C/001</td>
    <td><button onclick="openFile('vc')">Enter File</button></td>
  </tr>
  <tr>
    <td>2</td>
    <td>DVC (ASA)’s Office</td>
    <td>UoE/B/DOSA/DVASA/002</td>
    <td><button onclick="openFile('dvasa')">Enter File</button></td>
  </tr>
  <tr>
    <td>3</td>
    <td>DVC (A & F)’s Office</td>
    <td>UoE/B/DOSA/DVA&F/003</td>
    <td><button onclick="openFile('dva_f')">Enter File</button></td>
  </tr>
  <tr>
    <td>4</td>
    <td>DVC (PRE)’s Office</td>
    <td>UoE/B/DOSA/DVPRE/004</td>
    <td><button onclick="openFile('dvpre')">Enter File</button></td>
  </tr>
  <tr>
    <td>5</td>
    <td>Registrar – Academic Office</td>
    <td>UoE/B/DOSA/RGAC/005</td>
    <td><button onclick="openFile('rgac')">Enter File</button></td>
  </tr>
  <tr>
    <td>6</td>
    <td>Registrar – Administration Office</td>
    <td>UoE/B/DOSA/RGAD/006</td>
    <td><button onclick="openFile('rgad')">Enter File</button></td>
  </tr>
  <tr>
    <td>7</td>
    <td>Registrar – Planning Office</td>
    <td>UoE/B/DOSA/RGPL/007</td>
    <td><button onclick="openFile('rgpl')">Enter File</button></td>
  </tr>
  <tr>
    <td>8</td>
    <td>Finance Office</td>
    <td>UoE/B/DOSA/FINO/008</td>
    <td><button onclick="openFile('fino')">Enter File</button></td>
  </tr>
  <tr>
    <td>9</td>
    <td>Legal Affairs & Council Secretariat</td>
    <td>UoE/B/DOSA/LACS/009</td>
    <td><button onclick="openFile('lacs')">Enter File</button></td>
  </tr>
  <tr>
    <td>10</td>
    <td>Daily File</td>
    <td>UoE/B/DOSA/DLY/010</td>
    <td><button onclick="openFile('dly')">Enter File</button></td>
  </tr>
  <tr>
    <td>11</td>
    <td>Committee of Deans</td>
    <td>UoE/B/DOSA/COD/011</td>
    <td><button onclick="openFile('cod')">Enter File</button></td>
  </tr>
  <tr>
    <td>12</td>
    <td>Senate</td>
    <td>UoE/B/DOSA/SEN/012</td>
    <td><button onclick="openFile('sen')">Enter File</button></td>
  </tr>
  <tr>
    <td>13</td>
    <td>Performance Contracting Issues</td>
    <td>UoE/B/DOSA/PCC/013</td>
    <td><button onclick="openFile('pcc')">Enter File</button></td>
  </tr>
  <tr>
    <td>14</td>
    <td>ICT Issues</td>
    <td>UoE/B/DOSA/CT/014</td>
    <td><button onclick="openFile('ct')">Enter File</button></td>
  </tr>
  <tr>
    <td>15</td>
    <td>ISO Issues</td>
    <td>UoE/B/DOSA/ISO/015</td>
    <td><button onclick="openFile('iso')">Enter File</button></td>
  </tr>
  <tr>
    <td>16</td>
    <td>Purchasing Issues</td>
    <td>UoE/B/DOSA/PUR/016</td>
    <td><button onclick="openFile('pur')">Enter File</button></td>
  </tr>
  <tr>
    <td>17</td>
    <td>Financial Issues</td>
    <td>UoE/B/DOSA/FCL/017</td>
    <td><button onclick="openFile('fcl')">Enter File</button></td>
  </tr>
  <tr>
    <td>18</td>
    <td>Directorate of ODEL</td>
    <td>UoE/B/DOSA/ODEL/018</td>
    <td><button onclick="openFile('odel')">Enter File</button></td>
  </tr>
  <tr>
    <td>19</td>
    <td>Directorate of IGU</td>
    <td>UoE/B/DOSA/IGU/019</td>
    <td><button onclick="openFile('igu')">Enter File</button></td>
  </tr>
  <tr>
    <td>20</td>
    <td>Council Secretariat</td>
    <td>UoE/B/DOSA/COSE/020</td>
    <td><button onclick="openFile('cose')">Enter File</button></td>
  </tr>
<tr>
  <td>21</td>
  <td>Adhoc Committee (UMB)</td>
  <td>UoE/B/DOSA/AUMB/021</td>
  <td><button onclick="openFile('aumb')">Enter File</button></td>
</tr>
<tr>
  <td>22</td>
  <td>Alcohol & Drug Abuse</td>
  <td>UoE/B/DOSA/ADA/022</td>
  <td><button onclick="openFile('ada')">Enter File</button></td>
</tr>
<tr>
  <td>23</td>
  <td>BASH</td>
  <td>UoE/B/DOSA/BASH/023</td>
  <td><button onclick="openFile('bash')">Enter File</button></td>
</tr>
<tr>
  <td>24</td>
  <td>Bookshop</td>
  <td>UoE/B/DOSA/BKS/024</td>
  <td><button onclick="openFile('bks')">Enter File</button></td>
</tr>
<tr>
  <td>25</td>
  <td>Branding Committee</td>
  <td>UoE/B/DOSA/BRCO/025</td>
  <td><button onclick="openFile('brco')">Enter File</button></td>
</tr>
<tr>
  <td>26</td>
  <td>Building Committee</td>
  <td>UoE/B/DOSA/BDC0/026</td>
  <td><button onclick="openFile('bdc0')">Enter File</button></td>
</tr>
<tr>
  <td>27</td>
  <td>Careers Development</td>
  <td>UoE/B/DOSA/CDEV/027</td>
  <td><button onclick="openFile('cdev')">Enter File</button></td>
</tr>
<tr>
  <td>28</td>
  <td>Catering</td>
  <td>UoE/B/DOSA/CAT/028</td>
  <td><button onclick="openFile('cat')">Enter File</button></td>
</tr>
<tr>
  <td>29</td>
  <td>Chaplaincy</td>
  <td>UoE/B/DOSA/CHAP/029</td>
  <td><button onclick="openFile('chap')">Enter File</button></td>
</tr>
<tr>
  <td>30</td>
  <td>Departmental Meeting</td>
  <td>UoE/B/DOSA/DMTG/030</td>
  <td><button onclick="openFile('dmtg')">Enter File</button></td>
</tr>
<tr>
  <td>31</td>
  <td>Disability Mainstreaming Committee</td>
  <td>UDE/B/DOSA/DMCO/031</td>
  <td><button onclick="openFile('dmco')">Enter File</button></td>
</tr>
<tr>
  <td>32</td>
  <td>Disposal Committee</td>
  <td>UOE/B/DOSA/DICO/032</td>
  <td><button onclick="openFile('dico')">Enter File</button></td>
</tr>
<tr>
  <td>33</td>
  <td>Eldoret Town Campus</td>
  <td>UOE/B/DOSA/CELD/033</td>
  <td><button onclick="openFile('celd')">Enter File</button></td>
</tr>
<tr>
  <td>34</td>
  <td>Environmental</td>
  <td>UoE/B/DOSA/ENV/034</td>
  <td><button onclick="openFile('env')">Enter File</button></td>
</tr>
<tr>
  <td>35</td>
  <td>Equipment</td>
  <td>UoE/B/DOSA/EQPT/035</td>
  <td><button onclick="openFile('eqpt')">Enter File</button></td>
</tr>
<tr>
  <td>36</td>
  <td>Exhibition Committee</td>
  <td>UoE/B/DOSA/EXCO/036</td>
  <td><button onclick="openFile('exco')">Enter File</button></td>
</tr>
<tr>
  <td>37</td>
  <td>Field Trips</td>
  <td>UDE/B/DOSA/FLTP/037</td>
  <td><button onclick="openFile('fltp')">Enter File</button></td>
</tr>
<tr>
  <td>38</td>
  <td>Further Studies & Other Training</td>
  <td>UDE/B/DOSA/FSOT/038</td>
  <td><button onclick="openFile('fsot')">Enter File</button></td>
</tr>
<tr>
  <td>39</td>
  <td>Games and Sports</td>
  <td>UDE/B/DOSA/GSP/039</td>
  <td><button onclick="openFile('gsp')">Enter File</button></td>
</tr>
<tr>
  <td>40</td>
  <td>General</td>
  <td>UoE/B/DOSA/GNL/040</td>
  <td><button onclick="openFile('gnl')">Enter File</button></td>
</tr>
<tr>
  <td>41</td>
  <td>Gender, Equity & Diversity</td>
  <td>UoE/B/DOSA/GED/041</td>
  <td><button onclick="openFile('ged')">Enter File</button></td>
</tr>
<tr>
  <td>42</td>
  <td>Graduation</td>
  <td>UoE/B/DOSA/GRAD/042</td>
  <td><button onclick="openFile('grad')">Enter File</button></td>
</tr>
<tr>
  <td>43</td>
  <td>Guidance & Counseling</td>
  <td>UoE/B/DOSA/GDC/043</td>
  <td><button onclick="openFile('gdc')">Enter File</button></td>
</tr>
<tr>
  <td>44</td>
  <td>HELB</td>
  <td>UoE/B/DOSA/HELB/044</td>
  <td><button onclick="openFile('helb')">Enter File</button></td>
</tr>
<tr>
  <td>45</td>
  <td>HIV/AIDS Mainstreaming</td>
  <td>UoE/B/DOSA/HAMS/045</td>
  <td><button onclick="openFile('hams')">Enter File</button></td>
</tr>
<tr>
  <td>46</td>
  <td>Inaugural Lecture</td>
  <td>UoE/B/DOSA/ILEC/046</td>
  <td><button onclick="openFile('ilec')">Enter File</button></td>
</tr>
<tr>
  <td>47</td>
  <td>Job Placement</td>
  <td>UoE/B/DOSA/JOBP/047</td>
  <td><button onclick="openFile('jobp')">Enter File</button></td>
</tr>
<tr>
  <td>48</td>
  <td>Library</td>
  <td>UoE/B/DOSA/LIBR/048</td>
  <td><button onclick="openFile('libr')">Enter File</button></td>
</tr>
<tr>
  <td>49</td>
  <td>Maintenance & Extension (Estates)</td>
  <td>UoE/B/DOSA/MEXT/049</td>
  <td><button onclick="openFile('mext')">Enter File</button></td>
</tr>
<tr>
  <td>50</td>
  <td>Marketing & Publicity</td>
  <td>UoE/B/DOSA/MPUB/050</td>
  <td><button onclick="openFile('mpub')">Enter File</button></td>
</tr>
<tr>
  <td>51</td>
  <td>Memorandum of Understanding</td>
  <td>UoE/B/DOSA/MOU/051</td>
  <td><button onclick="openFile('mou')">Enter File</button></td>
</tr>
<tr>
  <td>52</td>
  <td>Orphans & Needy Students</td>
  <td>UoE/B/DOSA/ONS/052</td>
  <td><button onclick="openFile('ons')">Enter File</button></td>
</tr>
<tr>
  <td>53</td>
  <td>Pension</td>
  <td>UoE/B/DOSA/PEN/053</td>
  <td><button onclick="openFile('pen')">Enter File</button></td>
</tr>
<tr>
  <td>54</td>
  <td>Petty Cash</td>
  <td>UoE/B/DOSA/PETC/054</td>
  <td><button onclick="openFile('petc')">Enter File</button></td>
</tr>
<tr>
  <td>55</td>
  <td>Physical Facilities</td>
  <td>UoE/B/DOSA/PHYF/055</td>
  <td><button onclick="openFile('phyf')">Enter File</button></td>
</tr>
<tr>
  <td>56</td>
  <td>Postgraduate Students</td>
  <td>UoE/B/DOSA/PGST/056</td>
  <td><button onclick="openFile('pgst')">Enter File</button></td>
</tr>
<tr>
  <td>57</td>
  <td>President’s Award Programme</td>
  <td>UoE/B/DOSA/PRA/057</td>
  <td><button onclick="openFile('pra')">Enter File</button></td>
</tr>
<tr>
  <td>58</td>
  <td>PSSP</td>
  <td>UoE/B/DOSA/PSSP/058</td>
  <td><button onclick="openFile('pssp')">Enter File</button></td>
</tr>
<tr>
  <td>59</td>
  <td>Public Health Services</td>
  <td>UoE/B/DOSA/PHS/059</td>
  <td><button onclick="openFile('phs')">Enter File</button></td>
</tr>
<tr>
  <td>60</td>
  <td>Rattansi</td>
  <td>UoE/B/DOSA/RATT/060</td>
  <td><button onclick="openFile('ratt')">Enter File</button></td>
</tr>
<tr>
  <td>61</td>
  <td>Rules & Regulations</td>
  <td>UoE/B/DOSA/RURE/061</td>
  <td><button onclick="openFile('rure')">Enter File</button></td>
</tr>
<tr>
  <td>62</td>
  <td>Section Heads</td>
  <td>UoE/B/DOSA/SHED/062</td>
  <td><button onclick="openFile('shed')">Enter File</button></td>
</tr>
<tr>
  <td>63</td>
  <td>Security</td>
  <td>UoE/B/DOSA/SEC/063</td>
  <td><button onclick="openFile('sec')">Enter File</button></td>
</tr>
<tr>
  <td>64</td>
  <td>Staff Funeral</td>
  <td>UoE/B/DOSA/SFUN/064</td>
  <td><button onclick="openFile('sfun')">Enter File</button></td>
</tr>
<tr>
  <td>65</td>
  <td>Staff Medical</td>
  <td>UoE/B/DOSA/SMED/065</td>
  <td><button onclick="openFile('smed')">Enter File</button></td>
</tr>
<tr>
  <td>66</td>
  <td>Student Funeral</td>
  <td>UoE/B/DOSA/SFUN/066</td>
  <td><button onclick="openFile('sfun_student')">Enter File</button></td>
</tr>
<tr>
  <td>67</td>
  <td>Students Centre</td>
  <td>UoE/B/DOSA/SCEN/067</td>
  <td><button onclick="openFile('scen')">Enter File</button></td>
</tr>
<tr>
  <td>68</td>
  <td>Students Finance</td>
  <td>UoE/B/DOSA/SFIN/068</td>
  <td><button onclick="openFile('sfin')">Enter File</button></td>
</tr>
<tr>
  <td>69</td>
  <td>Students Medical</td>
  <td>UoE/B/DOSA/SMED/069</td>
  <td><button onclick="openFile('smed_student')">Enter File</button></td>
</tr>
<tr>
  <td>70</td>
  <td>Students Recommendation</td>
  <td>UoE/B/DOSA/SREC/070</td>
  <td><button onclick="openFile('srec')">Enter File</button></td>
</tr>
<tr>
  <td>71</td>
  <td>Public Complaints Committee</td>
  <td>UoE/B/DOSA/PCC/071</td>
  <td><button onclick="openFile('pcc_pub')">Enter File</button></td>
</tr>
<tr>
  <td>72</td>
  <td>Students Orientation</td>
  <td>UoE/B/DOSA/SORI/072</td>
  <td><button onclick="openFile('sori')">Enter File</button></td>
</tr>
<tr>
  <td>73</td>
  <td>Transport</td>
  <td>UoE/B/DOSA/TPT/073</td>
  <td><button onclick="openFile('tpt')">Enter File</button></td>
</tr>
<tr>
  <td>74</td>
  <td>UESO Constitution</td>
  <td>UoE/B/DOSA/UESC/074</td>
  <td><button onclick="openFile('uesc')">Enter File</button></td>
</tr>
<tr>
  <td>75</td>
  <td>University Choir</td>
  <td>UoE/B/DOSA/UCHR/075</td>
  <td><button onclick="openFile('uchr')">Enter File</button></td>
</tr>
<tr>
  <td>76</td>
  <td>Team Building</td>
  <td>UoE/B/DOSA/TB/076</td>
  <td><button onclick="openFile('tb')">Enter File</button></td>
</tr>
<tr>
  <td>77</td>
  <td>USAID</td>
  <td>UoE/B/DOSA/USAD/077</td>
  <td><button onclick="openFile('usad')">Enter File</button></td>
</tr>
<tr>
  <td>78</td>
  <td>Visitors & Visits</td>
  <td>UoE/B/DOSA/VIST/078</td>
  <td><button onclick="openFile('vist')">Enter File</button></td>
</tr>
<tr>
  <td>79</td>
  <td>Wardens</td>
  <td>UGE/B/DOSA/WARD/079</td>
  <td><button onclick="openFile('ward')">Enter File</button></td>
</tr>
<tr>
  <td>80</td>
  <td>Workshop</td>
  <td>UoE/B/DOSA/WKSP/080</td>
  <td><button onclick="openFile('wksp')">Enter File</button></td>
</tr>
<tr>
  <td>81</td>
  <td>Work Study</td>
  <td>UoE/B/DOSA/WORK/081</td>
  <td><button onclick="openFile('work')">Enter File</button></td>
</tr>
<tr>
  <td>82</td>
  <td>Clubs & Societies</td>
  <td>UoE/B/DOSA/CLSO/082</td>
  <td><button onclick="openFile('clso')">Enter File</button></td>
</tr>
<tr>
  <td>83</td>
  <td>Deferment</td>
  <td>UoE/B/DOSA/DEFE/083</td>
  <td><button onclick="openFile('defe')">Enter File</button></td>
</tr>
<tr>
  <td>84</td>
  <td>Election</td>
  <td>UoE/B/DOSA/ELEC/084</td>
  <td><button onclick="openFile('elec')">Enter File</button></td>
</tr>
<tr>
  <td>85</td>
  <td>Examination Irregularities</td>
  <td>UoE/B/DOSA/EXA/085</td>
  <td><button onclick="openFile('exa')">Enter File</button></td>
</tr>
<tr>
  <td>86</td>
  <td>Hostels</td>
  <td>UoE/B/DOSA/HOS/086</td>
  <td><button onclick="openFile('hos')">Enter File</button></td>
</tr>
<tr>
  <td>87</td>
  <td>Non-Residence</td>
  <td>UoE/B/DOSA/NRES/087</td>
  <td><button onclick="openFile('nres')">Enter File</button></td>
</tr>
<tr>
  <td>88</td>
  <td>Personnel Issues</td>
  <td>UoE/B/DOSA/PERS/088</td>
  <td><button onclick="openFile('pers')">Enter File</button></td>
</tr>
<tr>
  <td>89</td>
  <td>Staff Correspondence</td>
  <td>UoE/B/DOSA/SCOR/089</td>
  <td><button onclick="openFile('scor')">Enter File</button></td>
</tr>
<tr>
  <td>90</td>
  <td>Students Disciplinary</td>
  <td>UoE/B/DOSA/SDIS/090</td>
  <td><button onclick="openFile('sdis')">Enter File</button></td>
</tr>
<tr>
  <td>91</td>
  <td>Students Leave of Absence</td>
  <td>UoE/B/DOSA/SLOA/091</td>
  <td><button onclick="openFile('sloa')">Enter File</button></td>
</tr>
<tr>
  <td>92</td>
  <td>UESO Organization</td>
  <td>UoE/B/DOSA/UESO/092</td>
  <td><button onclick="openFile('ueso')">Enter File</button></td>
</tr>
<tr>
  <td>93</td>
  <td>University Newsletter</td>
  <td>UoE/B/DOSA/NL/093</td>
  <td><button onclick="openFile('nl')">Enter File</button></td>
</tr>
<tr>
  <td>94</td>
  <td>Students Welfare Policies</td>
  <td>UoE/B/DOSA/DPOL/094</td>
  <td><button onclick="openFile('dpol')">Enter File</button></td>
</tr>
<tr>
  <td>95</td>
  <td>Bursary Fund Committee</td>
  <td>UoE/B/DOSA/DFC/095</td>
  <td><button onclick="openFile('dfc')">Enter File</button></td>
</tr>
<tr>
  <td>96</td>
  <td>Publicity & Entertainment</td>
  <td>UoE/B/DOSA/PE/096</td>
  <td><button onclick="openFile('pe')">Enter File</button></td>
</tr>
<tr>
  <td>97</td>
  <td>Students Appeals</td>
  <td>UoE/B/DOSA/SAP/097</td>
  <td><button onclick="openFile('sap')">Enter File</button></td>
</tr>
<tr>
  <td>98</td>
  <td>Re-Admissions Applications</td>
  <td>UoE/B/DOSA/RA/098</td>
  <td><button onclick="openFile('ra')">Enter File</button></td>
</tr>
<tr>
  <td>99</td>
  <td>Industrial Linkages</td>
  <td>UoE/B/DOSA/INK/099</td>
  <td><button onclick="openFile('ink')">Enter File</button></td>
</tr>
<tr>
  <td>100</td>
  <td>Anti-Corruption Sensitization</td>
  <td>UoE/B/DOSA/CPC/100</td>
  <td><button onclick="openFile('cpc')">Enter File</button></td>
</tr>
<tr>
  <td>101</td>
  <td>Occupational Safety & Environment</td>
  <td>UoE/B/DOSA/OSHE/101</td>
  <td><button onclick="openFile('oshe')">Enter File</button></td>
</tr>
<tr>
  <td>102</td>
  <td>KUDSA</td>
  <td>UoE/B/DOSA/KDS/102</td>
  <td><button onclick="openFile('kds')">Enter File</button></td>
</tr>
<tr>
  <td>103</td>
  <td>Application for Exams</td>
  <td>UoE/B/DOSA/APE/103</td>
  <td><button onclick="openFile('ape')">Enter File</button></td>
</tr>
<tr>
  <td>104</td>
  <td>Special Exams</td>
  <td>UoE/B/DOSA/SPE/104</td>
  <td><button onclick="openFile('spe')">Enter File</button></td>
</tr>
<tr>
  <td>105</td>
  <td>Technical & Evaluation Committee</td>
  <td>UoE/B/DOSA/TCE/105</td>
  <td><button onclick="openFile('tce')">Enter File</button></td>
</tr>
<tr>
  <td>106</td>
  <td>Office & Space Allocation</td>
  <td>UoE/B/DOSA/OSA/106</td>
  <td><button onclick="openFile('osa')">Enter File</button></td>
</tr>
<tr>
  <td>107</td>
  <td>Budget File</td>
  <td>UoE/B/DOSA/BUD/107</td>
  <td><button onclick="openFile('bud')">Enter File</button></td>
</tr>
<tr>
  <td>108</td>
  <td>Approved Imprests</td>
  <td>UoE/B/DOSA/APR/108</td>
  <td><button onclick="openFile('apr')">Enter File</button></td>
</tr>
<tr>
  <td>109</td>
  <td>SC Members List & Contacts</td>
  <td>UoE/B/DOSA/SCLC/109</td>
  <td><button onclick="openFile('sclc')">Enter File</button></td>
</tr>
<tr>
  <td>110</td>
  <td>Mentorship Policy</td>
  <td>UoE/DOSA/MENT/110</td>
  <td><button onclick="openFile('ment')">Enter File</button></td>
</tr>
<tr>
  <td>111</td>
  <td>Activity Report</td>
  <td>UoE/B/DOSA/ACTR/111</td>
  <td><button onclick="openFile('actr')">Enter File</button></td>
</tr>
<tr>
  <td>112</td>
  <td>Research & Innovation</td>
  <td>UoE/B/DOSA/RES/112</td>
  <td><button onclick="openFile('res')">Enter File</button></td>
</tr>
<tr>
  <td>113</td>
  <td>Class Representatives</td>
  <td>UoE/B/DOSA/CREP/113</td>
  <td><button onclick="openFile('crep')">Enter File</button></td>
</tr>
<tr>
  <td>114</td>
  <td>Central Services</td>
  <td>UoE/B/DOSA/CNS/114</td>
  <td><button onclick="openFile('cns')">Enter File</button></td>
</tr>
  <!-- Continue the rest in the same format up to 114 -->
</table>




<div id="fileView" class="hidden">
  <h3 id="fileTitle"></h3>

  <label>Create / Select Year Folder:</label>
  <input type="number" id="yearInput" placeholder="e.g. 2026" />
  <button onclick="openYear()">Open Year</button>

  <div id="yearSection"></div>

  <button onclick="goBack()">⬅ Back to File List</button>
</div>

<script>
let currentFile = '';
let currentYear = '';

function openFile(fileKey) {
  currentFile = fileKey;
  document.querySelector('table').classList.add('hidden');
  document.getElementById('fileView').classList.remove('hidden');
  document.getElementById('fileTitle').innerText = fileKey === 'vc'
    ? "Vice-Chancellor’s Office File"
    : "DVC (ASA)’s Office File";
}

function goBack() {
  document.querySelector('table').classList.remove('hidden');
  document.getElementById('fileView').classList.add('hidden');
  document.getElementById('yearSection').innerHTML = '';
}

function openYear() {
  currentYear = document.getElementById('yearInput').value;
  if (!currentYear) return alert('Enter year');

  const key = currentFile + '_' + currentYear;
  const records = JSON.parse(localStorage.getItem(key) || '[]');

  document.getElementById('yearSection').innerHTML = `
    <div class="year-folder">
      <h4>Year: ${currentYear}</h4>
      <div class="actions">Add Daily Document Entry</div>
      <input placeholder="Folio Number" id="folio" />
      <input placeholder="Document Name" id="docName" />
      <input placeholder="Heading" id="heading" />
      <input type="date" id="date" />
      <button onclick="saveEntry('${key}')">Save</button>
      <h4>Stored Documents</h4>
      <ul id="docList"></ul>
    </div>
  `;

  const list = document.getElementById('docList');
  records.forEach(r => {
    const li = document.createElement('li');
    li.textContent = `${r.folio} | ${r.name} | ${r.heading} | ${r.date}`;
    list.appendChild(li);
  });
}

function saveEntry(key) {
  const records = JSON.parse(localStorage.getItem(key) || '[]');
  records.push({
    folio: folio.value,
    name: docName.value,
    heading: heading.value,
    date: date.value
  });
  localStorage.setItem(key, JSON.stringify(records));
  openYear();
}
</script>
<script>
/* ==============================
   File Registry Universal Script
   ============================== */

/* Example: Offices list (can match your main table S/NO list) */
const offices = [
  { id: 'vc', name: "Vice-Chancellor's Office" },
  { id: 'dvasa', name: "DVC (ASA)'s Office" },
  { id: 'dvaaf', name: "DVC (A & F)'s Office" },
  { id: 'dvpre', name: "DVC (PRE)'s Office" },
  // Add all other offices here with unique IDs
];

/* Example: documents database (date format: YYYY-MM-DD) */
const documentsDB = {
  dvasa: [
    { date: '2026-02-10', name: 'Staff Meeting Minutes', index: 'UoE/B/DOSA/DVASA/002/001' },
    { date: '2026-02-05', name: 'Performance Report', index: 'UoE/B/DOSA/DVASA/002/002' },
    { date: '2026-01-28', name: 'Budget Request', index: 'UoE/B/DOSA/DVASA/002/003' },
  ],
  vc: [
    { date: '2026-02-08', name: 'VC Circular', index: 'UoE/B/DOSA/VC/001/001' },
    { date: '2026-01-30', name: 'Annual Report', index: 'UoE/B/DOSA/VC/001/002' },
  ],
  // Add documents for other offices
};

/* =============================
   Render File Registry
   ============================= */
function renderFileRegistry(officeId) {
  const container = document.getElementById('fileRegistryContainer');
  const office = offices.find(o => o.id === officeId);
  const docs = documentsDB[officeId] || [];

  let html = `
    <h2>${office.name} File Registry</h2>
    
    <!-- Year Selection -->
    <div class="year-selection">
      <label for="academicYear">Select Academic Year:</label>
      <select id="academicYear" onchange="renderDocuments('${officeId}')">
        <option value="2025/2026">Academic Year 2025/2026</option>
        <option value="2024/2025">Academic Year 2024/2025</option>
        <option value="2023/2024">Academic Year 2023/2024</option>
      </select>
      <button onclick="renderDocuments('${officeId}')">Open Year</button>
    </div>

    <!-- Search Bar -->
    <div class="search-bar">
      <input type="text" id="documentSearch" placeholder="Search documents..." onkeyup="searchDocuments()">
    </div>

    <!-- Documents Table -->
    <table id="documentsTable" border="1" cellspacing="0" cellpadding="5">
      <thead>
        <tr>
          <th>Date</th>
          <th>Document Name</th>
          <th>File Index</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody id="documentsBody">
        <!-- Documents will be populated here -->
      </tbody>
    </table>

    <button onclick="backToFileList()">⬅ Back to File List</button>
  `;

  container.innerHTML = html;

  // Initially render documents
  renderDocuments(officeId);
}

/* =============================
   Populate Documents Table
   ============================= */
function renderDocuments(officeId) {
  const docs = documentsDB[officeId] || [];
  const tbody = document.getElementById('documentsBody');

  // Sort latest first
  const sortedDocs = docs.sort((a, b) => new Date(b.date) - new Date(a.date));

  let rows = '';
  sortedDocs.forEach(doc => {
    rows += `
      <tr>
        <td>${new Date(doc.date).toLocaleDateString()}</td>
        <td>${doc.name}</td>
        <td>${doc.index}</td>
        <td><button onclick="openDocument('${doc.index}')">Open</button></td>
      </tr>
    `;
  });

  tbody.innerHTML = rows;
  searchDocuments(); // Apply current search filter
}

/* =============================
   Search Documents
   ============================= */
function searchDocuments() {
  const input = document.getElementById('documentSearch');
  const filter = input.value.toLowerCase();
  const table = document.getElementById('documentsTable');
  const tr = table.getElementsByTagName('tr');

  for (let i = 1; i < tr.length; i++) { // skip header
    const td = tr[i].getElementsByTagName('td')[1]; // document name column
    if (td) {
      const txtValue = td.textContent || td.innerText;
      tr[i].style.display = txtValue.toLowerCase().includes(filter) ? '' : 'none';
    }
  }
}

/* =============================
   Document Open & Navigation
   ============================= */
function openDocument(docIndex) {
  alert('Opening document: ' + docIndex);
  // Replace with actual document open logic
}

function backToFileList() {
  const container = document.getElementById('fileRegistryContainer');
  container.innerHTML = ''; // Clear registry
  alert('Returning to main file list...');
  // Optionally, render your main table here
}

/* =============================
   Example: Open DVC (ASA) Registry
   ============================= */
// Call this function when user clicks the office button
// Example: renderFileRegistry('dvasa');
</script>

</body>
</html>
